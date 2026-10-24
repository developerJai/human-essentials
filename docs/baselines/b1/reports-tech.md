# Reports — Technical Documentation

The `reports` feature of Human Essentials provides two distinct capabilities for a bank organization:

1. **Operational summary reports** — nine date-range-filterable report pages (donations, purchases, distributions, product drives, manufacturer donations, itemized breakdowns, requests, and an activity graph), served by `ReportsController`.
2. **NDBN Annual Reports** — a persisted, recalculable year-end report composed of eight sections, served by `Reports::AnnualReportsController` and backed by the `AnnualReport` model and the `Reports` service module.

## Components

| File | Role |
|---|---|
| `app/controllers/reports_controller.rb` | Nine summary/itemized report actions, all scoped to `current_organization` and the selected date range |
| `app/controllers/reports/annual_reports_controller.rb` | `index`, `show` (HTML + CSV), `recalculate` for annual reports |
| `app/models/annual_report.rb` | Persisted annual report (JSON payload per org/year) |
| `app/services/reports.rb` | `Reports` module façade: builds all eight section reports, retrieves/caches the `AnnualReport` |
| `app/services/reports/*_report_service.rb` | Eight section services: diaper, warehouse, adult incontinence, period supply, other products, partner info, children served, summary |
| `app/services/exports/export_report_csv_service.rb` | Flattens a persisted annual report into a two-row CSV |
| `app/views/reports/*.html.erb` | One view per summary action, plus partials `_donation`, `_distribution`, `_purchase`, `_manufacturer`, `_product_drive` |
| `app/views/reports/annual_reports/{index,show}.html.erb` | Annual report list and per-year detail |

## ReportsController (summary reports)

Every action runs behind `before_action :setup_date_range_picker`, and each query is bounded by `helpers.selected_range` (the user-selected date range). Actions and the data each exposes:

- **`donations_summary`** — `@donations = current_organization.donations.during(selected_range)` and `@recent_donations = @donations.recent`. The view renders total items received, money raised, a **New Donation** button, recent donation rows (`_donation` partial: item total, source, relative time), and a "See more..." link to the donations index.
- **`manufacturer_donations_summary`** — donations filtered `by_source(:manufacturer)` plus `current_organization.manufacturers.by_donation_date(10, selected_range)` (top 10). The view sums `line_items.total` across manufacturer donations and shows the distinct manufacturer count (`group_by(&:manufacturer).count`), followed by recent manufacturers with per-manufacturer donation counts.
- **`purchases_summary`** — delegates to `Purchase.organization_summary_by_dates(current_organization, selected_range)` returning a struct consumed by the view: `amount_spent`, category splits (`diapers`, `period_supplies`, `adult_incontinence`, `other`), `total_items`, `recent_purchases`.
- **`product_drives_summary`** — loads the *same* data as `donations_summary` (`@donations`, `@recent_donations`); the view filters recents with `by_source(:product_drive)` and relies on helpers (`total_number_of_drives`, `total_received_from_product_drives`, `total_received_money_donations_from_product_drives`) for the headline numbers.
- **`itemized_donations`** — `DonationItemizedBreakdownService.new(organization:, donation_ids:).fetch`; table of Item / Total Donated / Total On Hand.
- **`itemized_distributions`** — `DistributionItemizedBreakdownService` over distributions (`includes(:partner)`) in range; table of Item / Total Distributed / Total On Hand, with the on-hand cell getting the `table-danger` class when `below_onhand_minimum`.
- **`distributions_summary`** — recent distributions in range; the view shows total distributed, a count of items scheduled for future distribution, a **New Distribution** button, and rows of "N items distributed to <partner_name>, X ago".
- **`activity_graph`** — builds `{"Received donations" => Σ, "Purchased" => Σ, "Distributed" => Σ}` by summing `LineItem.active` quantities where `itemizable` is the org's donations/purchases/distributions in range. The view feeds this hash to a Highcharts bar chart via a Stimulus `highchart` controller; an alert ("No distributions found for the selected date range.") renders when the hash is empty.
- **`itemized_requests`** — `RequestItemizedBreakdownService.call(organization:, request_ids:)`; table of Item (with optional unit), Total Requested, Total On Hand (`on_hand || 0`), with `table-danger` highlighting below minimum.

Private helpers `total_purchased_unformatted`, `total_distributed_unformatted`, and `total_received_donations_unformatted` each sum `LineItem.active` quantities scoped to the itemizable collection within the range.

## Annual reports

### Controller flow

- **`index`** — lists report years from `current_organization.earliest_reporting_year` up to, **but excluding**, the current year (`(foundation_year...@actual_year)`), and computes `@month_remaining_to_report = 12 - Time.current.month` which the view renders as "<year> (available in N months)".
- **`show`** — `before_action :validate_show_params` raises `not_found!` unless `params[:year].to_i.positive?`. Retrieves via `Reports.retrieve_report(organization:, year:)` and responds to:
  - `html` — renders each section (`@report.each_report`) as a titled table of entry name/value pairs, with **Recalculate Report** and **Export Report** buttons.
  - `csv` — `send_data Exports::ExportReportCSVService.new(reports: @report.all_reports).generate_csv, filename: "NdbnAnnuals-#{@year}-#{Time.zone.today}.csv"`.
- **`recalculate`** (POST) — calls `retrieve_report(..., recalculate: true)` and redirects to the report with notice `"Recalculated annual report!"`.

### `Reports` module and caching

`Reports.retrieve_report` does `AnnualReport.find_or_create_by(organization:, year:)`; if `all_reports` is blank **or** `recalculate` is passed, it computes `Reports.all_reports` and persists the result with `update!`. The report is therefore computed once and cached as JSON until explicitly recalculated.

`Reports.all_reports(year:, organization:)` returns eight section hashes, in order:

1. `DiaperReportService` — "Diapers"
2. `WarehouseReportService` — "Warehouse and Storage"
3. `AdultIncontinenceReportService` — "Adult Incontinence"
4. `PeriodSupplyReportService` — "Period Supplies"
5. `OtherProductsReportService` — "Other Items"
6. `PartnerInfoReportService` — "Partner Agencies and Service Area"
7. `ChildrenServedReportService` — "Children Served"
8. `SummaryReportService` — "Year End Summary"

Each service exposes `#report` returning `{name:, entries: {label => formatted value}}`.

### Section services — calculation details

**Diapers** (19 entries): disposable diapers distributed = loose line-item sum (`Item.disposable_diapers`) **plus** diapers inside distributed kits (raw SQL joining `line_items` twice through the kit's item, filtered on `kit_items.reporting_category = 'disposable_diapers'`); cloth diapers distributed; monthly average (total ÷ 12.0, rounded); product drive stats split by `virtual: false/true` (drive counts, diapers and cloth collected, money raised — note `money_raised` sums are divided by 100); donated/purchased disposable counts; percentage donated/purchased against total acquired (donated + purchased); money spent purchasing diapers (`amount_spent_on_diapers_cents / 100.0`); "Purchased from" = distinct `purchases.purchased_from` values joined with distinct vendor `business_name`s.

**Warehouse and Storage**: storage location count; total square footage as a string, suffixed with "(N locations do not have square footage entered)" when applicable; largest storage site type = `warehouse_type` of the location with the greatest non-nil square footage, with fallbacks "No warehouses with square footage entered" or "<name> - warehouse type not given".

**Adult Incontinence**: supplies distributed = loose AI line items + kit-contained AI items (raw SQL, `reporting_category = 'adult_incontinence'`); adults assisted per month = loose quantity ÷ `COALESCE(items.distribution_quantity, 50.0)` ÷ 12, plus a per-kit calculation over distributed kits containing AI items (÷ `distribution_quantity` default 1.0, ÷ 12); supplies per adult per month; list of AI item names; % donated / % bought against donated+purchased; money spent (`amount_spent_on_adult_incontinence_cents / 100.0`).

**Period Supplies**: distributed = loose `Item.period_supplies` + kit items whose `reporting_category` is in `('pads','tampons','period_liners','period_underwear','period_other')` via a parameterized `kit_items_calculation(itemizable_type, string_type)` used identically against distributions, purchases, and donations; types list; % donated / % bought; money spent (`amount_spent_on_period_supplies_cents / 100.0`).

**Other Items**: distributed quantity over `Item.other_categories`; % donated / % bought; money spent (`amount_spent_on_other_cents / 100.0`); alphabetized product list. (No kit component here.)

**Partner Agencies and Service Area**: number of partners with a profile; one dynamic entry per agency type — `"Agency Type: #{I18n.t agency, scope: [:partners_profile]}"` with tallied counts; "Zip Codes Served" = unique, sorted `zips_served` joined with commas.

**Children Served**: total children = `CEILING(SUM(quantity / COALESCE(items.distribution_quantity, 50)))` over loose disposable-diaper distributions, plus a kit-based subquery (`DISTINCT ON (distributions.id, line_items.id, kits.id)`) for kits containing disposables; average children monthly = total ÷ 12.0 rounded to 2 decimals; `Repackages diapers?` and `Monthly diaper distributions?` rendered as `Y`/`N` from organization flags.

**Year End Summary**: three year-over-year percentage deltas — donation count, `money_raised` sum, disposable diaper donation quantity — comparing `year - 1` to `year`. `percent_difference` returns `"0%"` when both are zero, `"+100%"` when the prior year is zero, otherwise a rounded, delimited percentage prefixed with `+` when non-negative.

### CSV export

`Exports::ExportReportCSVService#generate_csv_data` concatenates **all** entry keys across sections into a single header row and all values into a single data row (two rows total), accessed via string keys (`report['entries']`), i.e. it expects the JSON-round-tripped shape stored on `AnnualReport#all_reports`.

## AnnualReport model

```ruby
belongs_to :organization, inverse_of: :annual_reports
validates :year, numericality: { greater_than: 1900, less_than: 10_000 }
has_paper_trail
```

Columns: `id`, `all_reports :json`, `year :integer`, `organization_id`, timestamps. `#each_report` yields `(hash['name'], hash['entries'])` per section — again string-keyed access.

## Caveats and gotchas

- **Symbol vs. string keys**: section services build symbol-keyed hashes; `AnnualReport#each_report` and the CSV exporter read string keys. This works for data read back from the `json` column, but code paths that use freshly computed (not yet round-tripped) hashes in the same request depend on that serialization boundary.
- `product_drives_summary` loads the identical instance variables as `donations_summary`; the drive-specific aggregates come from view helpers, not the controller.
- `DiaperReportService#money_from_drives` uses integer division (`sum(:money_raised) / 100`), while other money figures divide by `100.0`.
- `DiaperReportService#percent_cloth_diapers_purchased` and `#percent_disposable_diapers_purchased` guard on the *purchased* count being zero but divide by the *total acquired* denominator — a zero denominator with non-zero purchases would raise.
- The itemized donations/distributions/requests views all pass `id: "purchases"` to the shared filtered card.
- `donations_summary.html.erb` contains a stray closing `</section>` tag.
- Annual report years are only listed for completed years (the range excludes the current year); `SummaryReportService` coerces `year.to_i` while the other services use the value as given.
