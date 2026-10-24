# Transfers — Technical Documentation

Transfers move inventory between two storage locations belonging to the same organization. The feature provides partial CRUD: transfers can be created, listed, viewed, and deleted, but never edited. All inventory movement is recorded through the event-sourcing system (`TransferEvent` / `TransferDestroyEvent`), so storage-location quantities are derived from the event stream rather than mutated directly by this feature's code.

## Code Map

| File | Role |
|---|---|
| `app/controllers/transfers_controller.rb` | `index`, `new`, `create`, `show`, `destroy`, `validate` actions |
| `app/models/transfer.rb` | `Transfer` model: associations, scopes, validations |
| `app/services/transfer_create_service.rb` | Transactional save + event publication |
| `app/services/transfer_destroy_service.rb` | Guarded destroy + reversal event |
| `app/services/exports/export_transfers_csv_service.rb` | CSV export with per-item columns |
| `app/events/transfer_event.rb` | Inventory event for a created transfer |
| `app/events/transfer_destroy_event.rb` | Zeroing/reversal event for a deleted transfer |
| `app/views/transfers/` | `index`, `new`, `show`, `_transfer_row`, `_validate_modal` |

## Model: `Transfer`

Table `transfers`: `id`, `comment` (string), `created_at`, `updated_at`, `from_id`, `organization_id`, `to_id`.

Associations:

```ruby
has_paper_trail
belongs_to :organization, inverse_of: :transfers
belongs_to :from, class_name: "StorageLocation", inverse_of: :transfers_from
belongs_to :to, class_name: "StorageLocation", inverse_of: :transfers_to
# alias so Itemizable (which expects storage_location) works — points at `from`
belongs_to :storage_location, class_name: "StorageLocation",
           inverse_of: :transfers_from, foreign_key: :from_id
```

Concerns: `Itemizable` (nested `line_items`, `combine!`, `total`, quantity validation helpers) and `Filterable` (powers `class_filter` in the controller). Versioning via PaperTrail (`has_paper_trail`).

Scopes:

- `from_location(location_id)` — `where(from_id: location_id)`
- `to_location(location_id)` — `where(to_id: location_id)`
- `during(range)` — `where(created_at: range)`

Custom validations (all fire on create, since transfers are never updated):

1. `storage_locations_belong_to_organization` — both `from` and `to` must be storage locations of the owning organization; otherwise adds "location must belong to organization" on the corresponding attribute.
2. `storage_locations_must_be_different` — `from_id == to_id` adds "location must be different than from location" on `:to`.
3. `from_storage_quantities` — builds `View::Inventory.new(organization_id)` and selects line items whose `quantity` exceeds `inventory.quantity_for(item_id:)`; if any, adds "location has insufficient inventory for <item names>" on `:from`. Note: the quantity check is per item across the inventory view, using the source location implicitly via the inventory view semantics.
4. `line_items_quantity_is_positive` — delegates to `line_items_quantity_is_at_least(1)` from `Itemizable`; zero or negative quantities are rejected.

## Controller: `TransfersController`

Strong parameters: `params.require(:transfer).permit(:from_id, :to_id, :comment, line_items_attributes: %i(item_id quantity _destroy))`. Filter params permit `:from_location` and `:to_location`.

### `GET /transfers` (`index`)

- Calls `setup_date_range_picker`, then loads `current_organization.transfers` with `line_items`, `from`, `to` eager-loaded, applies `class_filter(filter_params)` and `during(helpers.selected_range)`.
- Filter dropdown collections come from `StorageLocation.with_transfers_from(current_organization)` and `StorageLocation.with_transfers_to(current_organization)` — only locations that have actually been used in transfers appear.
- `format.csv` streams `Exports::ExportTransfersCSVService` output as `Transfers-<YYYY-MM-DD>.csv`.

### `GET /transfers/new` (`new`)

Builds an empty transfer with one line item. Collections: `storage_locations.active.alphabetized` and `items.active.alphabetized`.

### `POST /transfers` (`create`)

```ruby
@transfer = current_organization.transfers.new(transfer_params)
@transfer.line_items.combine!   # merges duplicate item rows
TransferCreateService.call(@transfer)
redirect_to transfers_path, notice: "#{@transfer.line_items.total} items have been transferred from #{@transfer.from.name} to #{@transfer.to.name}!"
```

Any `StandardError` (including validation failure raised by the service) is rescued: the message is placed in `flash.now[:error]`, form collections are reloaded (note: `load_form_collections` uses `items.alphabetized` *without* `.active`, unlike `new`), an empty line item is built if needed, and `new` is re-rendered.

### `GET /transfers/:id` (`show`)

Loads the transfer with line items, locations, and items; exposes `@total = @transfer.line_items.total` and `@line_items = @transfer.line_items.sorted`.

### `DELETE /transfers/:id` (`destroy`)

Delegates to `TransferDestroyService.new(transfer_id: params[:id]).call`, which returns a `Result`. Success flashes "Successfully deleted Transfer #<id>!"; failure flashes the error message. Always redirects to the index.

### `POST /transfers/validate` (`validate`, JSON)

Pre-submission validation used by the confirmation modal (Stimulus `confirmation` controller with `data-confirmation-pre-check-path-value` pointing at `validate_transfers_path(format: :json)`). Builds the transfer from params, combines line items, and:

- valid → `{valid: true, body: <rendered transfers/validate_modal partial>}`
- invalid → `{valid: false}` with HTTP status `unprocessable_content` (422)

## Services

### `TransferCreateService.call(transfer)`

```ruby
if transfer.valid?
  ActiveRecord::Base.transaction do
    transfer.save
    TransferEvent.publish(transfer)
  end
else
  raise StandardError.new(transfer.errors.full_messages.join(", "))
end
```

Save and event publication are atomic; an invalid transfer surfaces its full validation messages as the exception message shown in the flash.

### `TransferDestroyService`

- Guard: `Audit.finalized_since?(transfer, transfer.to_id, transfer.from_id)` — if a finalized audit touched either location since the transfer was made, raises *"We can't delete this transfer because its items were audited since you made the transfer."*
- Otherwise, within a transaction: `TransferDestroyEvent.publish(transfer)` then `transfer.destroy!`.
- Returns `Result.new` on success or `Result.new(error: e)` on any `StandardError`.

## Events (inventory integration)

- `TransferEvent.publish(transfer)` creates an `Event` with `group_id: "transfer-#{transfer.id}-#{SecureRandom.hex}"` and an `EventTypes::InventoryPayload` built from `EventTypes::EventLineItem.from_line_items(transfer.line_items, from: transfer.from.id, to: transfer.to.id)` — i.e., each line item moves quantity from the source to the destination location.
- `TransferDestroyEvent.publish(transfer)` creates the reversal with `group_id: "transfer-destroy-..."` using `EventLineItem.zeroed_line_items(..., to:, from:)`, undoing the movement when a transfer is deleted.

## CSV Export

`Exports::ExportTransfersCSVService#generate_csv` emits:

- Base columns: `From`, `To`, `Date` (`%F`), `Comment` (literal `"none"` when nil), `Total Moved` (`line_items.total`).
- One additional column per distinct organization item name (`DISTINCT ON (LOWER(name))`, ordered `LOWER(name) ASC`), initialized to `0`; each line item's quantity is **added** to its item column (quantities accumulate if duplicates survive). Line items whose item name is not among the headers are skipped (`next unless item_column_idx`).

## Views / UX notes

- **Index**: "Inventory Transfers" header; filter card with "From this storage location", "To this storage location", and a date-range picker; `Filter`/`Clear` buttons; "Export Transfers" (only rendered when `@transfers.any?`) and "New Transfer" buttons. Table columns: From, To, Date, Comment, Total Moved, Actions (delete with confirm "Are you sure you want to permanently remove this transfer?", and view).
- **New**: simple_form with `from` (via the shared `storage_locations/source` partial, error hint "Which location are you moving inventory from?"), `to` (hint "Which location is receiving this?"), `comment`, and a line-items fieldset ("Items in this transfer") supporting "Add Another Item" and barcode entry (`data-capture-barcode="true"`, plus the shared barcode modal partial). Submit triggers `click->confirmation#openModal`: the form is validated server-side first, and the returned `_validate_modal` (item/quantity table, optional comment, "No, I need to make changes" / "Yes, it's correct") is displayed before the real POST.
- **Show**: card titled "Transfer from <from> to <to> on <MM/DD/YYYY>" with an item/quantity table, a Total row, and a Comments row when present.

## Caveats for developers

- There is no `edit`/`update` action — correcting a transfer means deleting it (if allowed) and re-creating it.
- Deletion is blocked after a finalized audit of either involved location.
- `line_items.combine!` runs in both `create` and `validate`, so duplicate item rows are merged before validation.
- On create-failure re-render, the items dropdown includes inactive items (`load_form_collections` omits `.active`) — a subtle inconsistency with `new`.
- Transfers are versioned with PaperTrail, but inventory truth lives in the event stream.
