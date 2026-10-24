# Distributions — Technical Documentation

Distributions are the primary mechanism by which inventory leaves a diaper bank in Human Essentials. A distribution issues a set of items from a single storage location to a single partner organization. This document describes the implementation for developers.

## Domain Model

### `Distribution` (`app/models/distribution.rb`)

Table: `distributions`

| Column | Type | Notes |
|---|---|---|
| `id` | integer | PK |
| `agency_rep` | string | Free-text agency representative |
| `comment` | text | |
| `delivery_method` | integer enum | `pick_up: 0` (default), `delivery: 1`, `shipped: 2`; `NOT NULL` |
| `issued_at` | datetime | Scheduled distribution date/time |
| `reminder_email_enabled` | boolean | default `false`, `NOT NULL` |
| `shipping_cost` | decimal(8,2) | Only meaningful when `shipped` |
| `state` | integer enum | `scheduled: 5`, `complete: 10`; default `scheduled`, `NOT NULL` |
| `organization_id`, `partner_id`, `storage_location_id` | integer | FKs |

Associations and mixins:

- `belongs_to :storage_location` — distributions are issued from exactly one storage location so on-hand amounts can be verified.
- `belongs_to :partner`, `belongs_to :organization`.
- `has_one :request, dependent: :nullify` with `accepts_nested_attributes_for :request` — a distribution may fulfill a partner request.
- Concerns: `Itemizable` (line items), `Exportable`, `IssuedAt`, `Filterable`, plus `ItemsHelper`; versioned with `has_paper_trail`.

Validations and callbacks:

- `delivery_method` presence.
- Custom validation `line_items_quantity_is_positive` — total line-item quantity must be at least 1.
- `shipping_cost` must be `>= 0` (allow blank) but only when `shipped?`.
- `before_save :combine_distribution` — merges duplicate line items (`line_items.combine!`).
- `before_save :reset_shipping_cost` — nils out `shipping_cost` unless `delivery_method == "shipped"`.
- `before_destroy :check_no_intervening_snapshot` — raises `"We can't delete distributions entered before <date>."` when a `SnapshotEvent` intervenes between the distribution and now, preventing deletion of distributions older than the last inventory snapshot.

Notable scopes: `active` (only active items), `with_diapers`, `with_period_supplies`, `by_item_id`, `by_item_category_id`, `by_reporting_category`, `by_partner`, `by_location`, `by_state`, `recent(count = 3)`, `future` (issued tomorrow or later), `during(range)`, `apply_filters`, `this_week`, `in_last_12_months`.

Notable methods:

- `copy_from_request(request)` — builds a distribution from a partner request: copies organization, partner, sets `agency_rep` to the requesting partner user's formatted email, copies request comments, defaults `issued_at` to tomorrow, and builds a line item per `item_request`. If an item request has a custom `request_unit`, the quantity is deliberately left blank so staff must enter it.
- `copy_from_donation(donation_id, storage_location_id)` — pre-populates line items from a donation.
- `initialize_request_items` — used by the edit page; links line items to their originating item requests and adds zero-quantity line items for any requested items missing from the distribution.
- `distributed_at` — formats `issued_at` as date-only when the time component is midnight, otherwise date + time.
- `future?` / `past?` — compare `issued_at` to today.
- `csv_export_attributes` — partner name, issue date, storage location, total quantity, total value in dollars, delivery method, state, agency rep.

## Service Layer

All distribution services inherit from `DistributionService` (`app/services/distribution_service.rb`), which wraps the work in a DB transaction via `perform_distribution_service`, rescues `ActiveRecord::RecordNotFound`, `Errors::InsufficientAllotment` (attaching insufficiency errors to the offending line items), and `StandardError`, and exposes `success?` / `error`. The service always returns `self`.

- **`DistributionCreateService.new(distribution, request_id = nil).call`** — saves the distribution, publishes a `DistributionEvent`, and when fulfilling a request, marks it `status: 'fulfilled'` and ties it to the distribution. Guards against double-fulfillment: raises `"Request has already been fulfilled by Distribution <id>"`. If the partner has `send_reminders`, enqueues `PartnerMailerJob.perform_later` to notify the partner.
- **`DistributionUpdateService.new(old_distribution, params).call`** — drops line-item attributes with zero quantity, then delegates to `ItemizableUpdateService` with `event_class: DistributionEvent`. Tracks old/new `issued_at` and `delivery_method`; `resend_notification?` is true when the issue *date* changed, the delivery method changed, or the item contents changed (computed by `DistributionContentChangeService`).
- **`DistributionDestroyService.new(distribution_id).call`** — publishes a `DistributionDestroyEvent` (zeroed line items, which restores inventory) and then `destroy!`s the record.
- **`DistributionContentChangeService`** — diffs old vs new line-item sets by `item_id`; exposes `updates` (name, old/new quantity), `removed`, `any_change?`, and `changes`.
- **`DistributionTotalsService.call(distributions)`** — returns `Hash<Integer, DistributionTotal(quantity, value)>` computed in SQL with window functions (`SUM ... OVER (PARTITION BY distributions.id)`); values use `items.value_in_cents * line_items.quantity`. Quantities/values shrink when item filters are applied.
- **`DistributionItemizedBreakdownService.new(organization:, distribution_ids:)`** — `fetch` returns per-item totals distributed with current on-hand quantity, on-hand minimum, and a `below_onhand_minimum` flag (from `View::Inventory`); `fetch_csv` renders CSV with headers `Item`, `Total Distribution`, `Total On Hand`.
- **`Exports::ExportDistributionsCSVService`** — builds the distributions CSV. Base columns: Partner, Initial Allocation (`created_at`), Scheduled for (`issued_at` falling back to `created_at`), Source Inventory, a filter-aware quantity column (`Total Items` or `Total Number of <item/category/reporting category>`), a filter-aware value column, Delivery Method, Shipping Cost, Status, Agency Representative, Comments, Reporting Category. Then one column per organization item, optionally interleaved with `<Item> In-Kind Value` (if `organization.include_in_kind_values_in_exported_files`) and `<Item> Packages` (if `organization.include_packages_in_distribution_export`).
- **`CalendarService.calendar(organization_id)`** — generates an ICS feed (via `icalendar`) of the organization's distributions issued within the last year. Each event is 15 minutes long, summary `"Pickup from <partner>"`, location = storage location address, with proper VTIMEZONE blocks per storage-location time zone. `CalendarService.time_zones` returns a curated, offset-sorted zone list for selects.
- **`DeadlineService`** — computes the next monthly deadline date from a `deadline_day`; `DeadlineService.get_deadline_for_partner(partner)` prefers the partner group's `deadline_day`, falling back to the organization's.

## Event Sourcing

Inventory changes are event-sourced:

- `DistributionEvent.publish(distribution)` — creates an `Event` with an `EventTypes::InventoryPayload` whose line items are drawn **from** the distribution's storage location (inventory decrement). `group_id` is `"dist-<id>-<hex>"`.
- `DistributionDestroyEvent.publish(distribution)` — publishes zeroed line items for the same location (inventory restore). `group_id` is `"dist-destroy-<id>-<hex>"`.

## Controllers

### `DistributionsController` (`app/controllers/distributions_controller.rb`)

Includes `DateRangeHelper`, `DistributionHelper`, `Validatable`. Turbo is enabled for `new` and `show`. The `calendar` action skips authentication, user authorization, and the organization requirement entirely.

| Action | Behavior |
|---|---|
| `index` | Lists org distributions ordered by `issued_at` desc with filters (item, item category, reporting category, partner, state, storage location, date range). Computes paginated and overall totals via `DistributionTotalsService`, flags distributions containing inactive items, and highlights the distribution just created (session `created_distribution_id`). CSV format streams `Exports::ExportDistributionsCSVService` as `Distributions-<date>.csv`. |
| `new` | Builds a distribution either from a request (`copy_from_request`) or optionally from a donation (`copy_from_donation`). Only active storage locations with positive inventory are offered. |
| `validate` | POST endpoint backing the pre-create confirmation modal. Builds (but does **not** save) the distribution, combines line items, and returns `{valid: true, body: <modal HTML>}` or `{valid: false}`. |
| `create` | Runs `DistributionCreateService`. On success: stores highlight id in session, runs `InventoryCheckService` (flashing minimum/recommended inventory alerts), schedules the reminder email, and redirects with "Distribution created!". On failure: rebuilds form state (request items, items, non-deactivated partners, positive-inventory locations) and re-renders via Turbo Stream with status 400 and flash `"Sorry, we weren't able to save the distribution. \n <details>"`. |
| `show` | Loads line items, total quantity, and total package count (nil when zero). |
| `edit` | Permitted only when the distribution is not complete **and** is in the future, or the current user has the org-admin role; otherwise redirects with an error. Computes `@changes_disallowed` when a `SnapshotEvent` intervenes, and `@audit_warning` when an audit at that storage location is newer than the distribution. Offers storage locations whose inventory is non-negative. |
| `update` | Runs `DistributionUpdateService`. On success, if `resend_notification?` and the partner has reminders enabled, sends "Your Distribution Has Changed" via `PartnerMailerJob.perform_now` with the content diff; re-schedules the reminder email; runs the inventory check. |
| `destroy` | Runs `DistributionDestroyService`; flash "Distribution <id> has been reclaimed!". |
| `print` | Streams `DistributionPdf` inline as `"<partner> <sortable date>.pdf"`. |
| `itemized_breakdown` | CSV-only: `DistributionItemizedBreakdownService` for the selected date range, as `Itemized-Breakdown-Distributions-<date>.csv`. |
| `schedule` | HTML calendar page; JSON returns pickups between `params[:start]` and `params[:end]`. |
| `calendar` | Unauthenticated ICS feed. The URL carries the org id encrypted with `ActiveSupport::MessageEncryptor` keyed on the first 32 bytes of `secret_key_base`; invalid signatures return 401. |
| `picked_up` | Marks a scheduled distribution `complete!`; flashes success or error. |
| `pickup_day` | Lists distributions for one day (default today) plus aggregated per-item totals (`daily_items`: name, quantity, package count). |

Permitted params: `comment, agency_rep, issued_at, partner_id, storage_location_id, reminder_email_enabled, delivery_method, shipping_cost`, plus `line_items_attributes: [item_id, quantity, _destroy]`, and a nested `request_attributes[:id]`.

Reminder scheduling (`schedule_reminder_email`): skipped when the distribution is past or the partner has reminders off; otherwise `DistributionMailer.reminder_email` is enqueued with `deliver_later(wait_until: issued_at - 1.day)`.

### `DistributionsByCountyController`

`report` renders "Estimated Distributions by County" for the selected date range using `DistributionSummaryByCountyQuery.call(organization_id:, start_date:, end_date:)` (ISO8601 UTC strings). The query (raw SQL, `app/queries/distribution_summary_by_county_query.rb`) computes per-distribution totals, joins partners → profiles → served areas → counties, multiplies by each county's `client_share / 100` (defaulting to 100%), labels county-less value as `Unspecified` (region `ZZZ` so it sorts last), always unions in an `Unspecified` row, and returns `CountySummary(name, quantity, value)` rows grouped by county.

## Mailers

`DistributionMailer` (`app/mailers/distribution_mailer.rb`):

- `partner_mailer(org, distribution, subject, distribution_changes)` — aborts for past distributions or deactivated partners. Recipient is the request's requester email when present, otherwise the partner email; CC includes the partner email plus the profile's pick-up emails for pick-up distributions. Body uses the organization's default email text run through `TextInterpolatorService` (variables: delivery method "delivered"/"picked up", distribution date, partner name, comment), lists item updates/removals when contents changed, and attaches the distribution PDF. Subject: `"<subject> from <org name>"`.
- `reminder_email(distribution_id)` — aborts when past, reminders disabled, or partner deactivated. Subject `"<partner> Distribution Reminder"`; body states tomorrow is the distribution pick up/delivery date.

## PDF

`DistributionPdf` (Prawn) renders the distribution manifest: org logo (uploaded logo or default), org name/address/email, partner primary contact, "Issued to", a delivery address block (preferring the profile's program address) for delivery/shipped methods, "Issued on" (`distributed_at`), optional "Items Received Year-to-Date" (org setting `ytd_on_distribution_printout`), distribution ID, comments, then the item table. With a request: columns Items Received / Requested / Received / Value-per-item / In-Kind Value Received / Packages, including requested-but-not-received rows; without: Items Received / Value/item / In-Kind Value / Quantity / Packages. Org settings `hide_value_columns_on_receipt` and `hide_package_column_on_receipt` strip columns; `signature_for_distribution_pdf` appends "Received By:" / "Delivered By:" signature lines. Request quantities render with units when the `enable_packs` Flipper flag is on.

## Views & Front-End Behavior

- **Index** (`app/views/distributions/index.html.erb`): filter card, "Export Distributions" CSV button, "New Distribution" button, table with per-row actions (View, View Request, Edit when `(!complete && !future) || org admin`, Print, Reclaim with confirmation). Rows and totals adapt column headers to the active item/category filter. Rows with inactive items disable Edit/Reclaim and show "Has Inactive Items".
- **Form** (`_form.html.erb`): partner select (locked when backed by a request — the id travels via hidden field since disabled inputs don't submit), datetime picker (15-minute steps), "Send email reminder the day before?" checkbox, agency representative, delivery-method radios with a shipping-cost field toggled by a Stimulus `distribution-delivery` controller, storage-location source selector, comment, and dynamic line items with "Add Another Item". Submission opens a confirmation modal (Stimulus `confirmation` controller) backed by the `validate` action; the modal lists partner, storage location, and items with "Yes, it's correct" / "No, I need to make changes".
- **Edit** warnings: a notice when editing past-dated distributions, and an audit warning advising a manual inventory adjustment when an audit postdates the distribution.
- **Schedule** (`schedule.html.erb` + `schedule.json.jbuilder`): FullCalendar-style calendar fed by the JSON action (events titled by partner, classed `fc-dist-complete` / `fc-dist-scheduled`, linking to the pickup-day page) plus a "Copy Calendar URL to clipboard" button exposing the encrypted ICS URL (`DistributionHelper#hashed_calendar_path`).
- **Pickup day** (`pickup_day.html.erb`): the day's pickups (partner, time, source, total items, status, "Distribution Complete" action) and aggregated item totals.
- **Show**: summary table, line-item table with totals, buttons "Distribution Complete" (when scheduled), "Make a Correction" (future or org admin; disabled when any item is inactive, with explanatory warning), and Print.

`DistributionHelper` also provides `distribution_shipping_cost` (currency or blank when zero/nil) and pickup-date param parsing.

## Gotchas

- `print.html.erb` is scaffold filler; printing actually responds with the PDF via `format.any`.
- The index controller comment flags redundant status filtering (`@statuses` vs `@selected_status`) with a FIXME.
- Shipping cost is silently cleared on save for non-shipped delivery methods.
- Distribution deletion and content edits are blocked once a `SnapshotEvent` postdates the distribution.
- The ICS calendar endpoint is public by design; security rests on the encrypted hash parameter.
