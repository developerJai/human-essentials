# Adjustments — Technical Documentation

Adjustments are the mechanism Essentials Banks use to fix incorrect inventory totals at Storage Locations. An adjustment records a set of manual increases and/or decreases to item quantities at a single storage location, attributed to the user who made it.

## Code Map

| Concern | File |
|---|---|
| Controller | `app/controllers/adjustments_controller.rb` |
| Model | `app/models/adjustment.rb` |
| Create service | `app/services/adjustment_create_service.rb` |
| CSV export | `app/services/exports/export_adjustments_csv_service.rb` |
| Inventory event | `app/events/adjustment_event.rb` |
| Views | `app/views/adjustments/{index,new,show}.html.erb` |

## Data Model

Table `adjustments`:

| Column | Type | Notes |
|---|---|---|
| `id` | integer | PK |
| `comment` | text | Free-text reason for the adjustment |
| `organization_id` | integer | Owning bank |
| `storage_location_id` | integer | Location being adjusted |
| `user_id` | bigint | User who created the adjustment |
| `created_at` / `updated_at` | datetime | NOT NULL |

`Adjustment`:

- `has_paper_trail` — versioned via PaperTrail.
- `belongs_to :organization`, `belongs_to :storage_location`, `belongs_to :user`.
- Includes `Exportable`, `Itemizable` (provides `line_items`, each with `item_id` and signed `quantity`), and `Filterable`.
- Scopes: `at_location(location_id)`, `by_user(user_id)`, `during(range)` (filters on `adjustments.created_at`).
- Custom validation `storage_locations_belong_to_organization`: when an organization is present, the chosen storage location must be one of the organization's storage locations, otherwise the error `storage_location: storage location must belong to organization` is added.

Line items carry the sign of the change: a positive `quantity` increases inventory, a negative `quantity` decreases it.

### `Adjustment#split_difference`

Partitions line items into positive and negative sets and returns a pair of new in-memory adjustments `[increasing_adjustment, decreasing_adjustment]`, with the decreasing adjustment's quantities multiplied by `-1` so both halves hold positive numbers. **Caveat:** the negation mutates the line items shared with the original adjustment (noted by an inline comment in the source).

### `Adjustment.generate_csv(adjustments)`

Returns `nil` for an empty collection; otherwise delegates to `Exports::ExportAdjustmentsCSVService.generate_csv(adjustments, adjustments.first.organization)`.

## Controller & Routes

`AdjustmentsController` provides deliberately limited CRUD: `index`, `show`, `new`, `create`. There is no edit, update, or destroy — adjustments are immutable once created.

- `GET /adjustments` (`index`, HTML and CSV): sets up the date-range picker; loads `current_organization.adjustments.order(created_at: :desc).class_filter(filter_params).during(helpers.selected_range)`; paginates with `includes(:line_items, :storage_location)` via `page(params[:page])`. Filter dropdown sources: `StorageLocation.with_adjustments_for(current_organization)` (id/name only) and `current_organization.users`. CSV responds with `Adjustment.generate_csv(@adjustments)` as `Adjustments-<today>.csv`.
- `GET /adjustments/:id` (`show`): finds within `current_organization.adjustments` (org-scoped lookup).
- `GET /adjustments/new` (`new`): builds a new adjustment with one blank line item; `@storage_locations = current_organization.storage_locations.active`; `@items = current_organization.items.loose.active.alphabetized` (kits are excluded — loose items only).
- `POST /adjustments` (`create`): calls `AdjustmentCreateService.new(adjustment_params.merge(organization: current_organization, user: current_user)).call`. On success flashes "Adjustment was successful." and redirects to the show page. On failure it flashes each error as `"attribute: message"` joined with `<br />`, reloads form collections, and re-renders `new`. Note: the failure path's `load_form_collections` uses `current_organization.items.loose.alphabetized` — without `.active`, unlike `new`.

Strong params: `storage_location_id`, `comment`, `organization_id`, plus `line_items_attributes: [item_id, quantity, _destroy]`.

`filter_params` (also a helper method) permits `:at_location` and `:by_user` under the `filters` key.

## Create Flow

`AdjustmentCreateService#call`:

1. `combine_adjustment` — `@adjustment.line_items.combine!` merges duplicate line items for the same item.
2. If `@adjustment.valid? && enough_inventory_for_decreases?`, opens a transaction, saves the adjustment, and publishes `AdjustmentEvent.publish(adjustment)`.
3. Rescues `Errors::InsufficientAllotment` and `InventoryError` inside the transaction: adds the exception message to `errors[:base]` and raises `ActiveRecord::Rollback`, so an adjustment that would drive inventory negative is not persisted.
4. Returns `self`; the controller inspects `result.adjustment.errors`.

### Known issues in the service

- `enough_inventory_for_decreases?` is defined **outside** the class body (after the class's `end`), making it a top-level/Object private method rather than a class member. It still resolves when invoked from `call`.
- Its loop body is a no-op: `next unless line_item.quantity.negative?` is followed by nothing, so the method only checks that a storage location is present (returns `false` when `nil`) and that `@adjustment.errors` is empty. Real insufficiency enforcement happens via the event layer raising `Errors::InsufficientAllotment` / `InventoryError` during `AdjustmentEvent.publish`.

## Event Sourcing

`AdjustmentEvent < Event`. `publish(adjustment)` creates an event with:

- `eventable: adjustment`
- `group_id: "adjustment-#{adjustment.id}-#{SecureRandom.hex}"`
- `organization_id`, `event_time: Time.zone.now`
- `data: EventTypes::InventoryPayload` whose items come from `EventTypes::EventLineItem.from_line_items(adjustment.line_items, to: adjustment.storage_location_id)` — i.e. signed deltas applied *to* the adjusted storage location.

Inventory totals are therefore derived through the event-sourced inventory aggregate, not written directly by the adjustment.

## CSV Export

`Exports::ExportAdjustmentsCSVService.generate_csv(adjustments, organization)` builds a CSV with headers `Created date`, `Storage Area`, `Comment`, `Updates`, followed by one column per distinct organization item name (ordered by name). Per row:

- `Created date` — `created_at` as `%F` (YYYY-MM-DD)
- `Storage Area` — storage location name
- `Comment` — adjustment comment
- `Updates` — count of line items with non-zero quantity
- Item columns — summed signed quantity per item name, `0` where the item wasn't touched.

## UI Notes

- **Index** (`Inventory Adjustments`): filter card with "Filter by Storage Location", user filter, and a date-range picker; "Filter" / "Clear Filters" buttons; "Export Adjustments" (rendered only when adjustments exist, carries current filters into the CSV request) and "New Adjustment" buttons. Table columns: Created, Storage location, Comment, Summary (pluralized "N changes"), Actions (View). Kaminari pagination in the footer.
- **New** (`New Inventory Adjustment`): instructional copy — enter a negative quantity to subtract an item, a plain positive amount to add. Storage-location picker (rendered with `include_omitted_items: true`), a Comment field, an "Items in this adjustment" fieldset with "Add Another Item", barcode capture enabled (`data-capture-barcode="true"` plus the barcode modal partial).
- **Show**: lists each line item as "Added"/"Removed" with the item name and absolute quantity (rows CSS-classed `positive`/`negative`), followed by Organization, Storage location, and Comments.

## Gotchas for Developers

| Gotcha | Detail |
|---|---|
| Immutable records | No update/destroy routes or actions; to correct a mistake, create a compensating adjustment. |
| Loose items only | The item picker excludes kit items (`items.loose`). |
| `split_difference` mutates | Negation of decreasing quantities alters the original adjustment's in-memory line items. |
| Active-scope drift | `new` uses `.active` items; the `create` failure re-render does not. |
| Empty CSV | `Adjustment.generate_csv` returns `nil` when the filtered set is empty; the UI avoids this by hiding the export button. |
