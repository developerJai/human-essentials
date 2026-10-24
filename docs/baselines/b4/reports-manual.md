# Reports — User Manual

> Step-by-step instructions for using Reports.

---

## Prerequisites

- A login for your organization — every report shows only your own organization's data
- Donations, purchases, and distributions already recorded, since all report figures come from those records
- On-hand minimums set on your items if you want low-stock items highlighted in red in the itemized reports

---

## Overview

This guide walks operations staff through the two halves of Reports: the nine everyday summary pages (donations, manufacturer donations, purchases, product drives, distributions, the item-by-item breakdown tables, and the Activity Graph), and the yearly NDBN Annual Report workflow — opening a completed year, recalculating it after corrections, and exporting it as a CSV spreadsheet.

---

## Task 1: Read an everyday summary report

### Steps

1. Open the summary page you need — **Donations (All Sources)**, **Manufacturer Donations**, **Purchases**, **Product Drives**, or **Distributions**.
2. Set the date range — every figure on the page follows the range you pick.
3. Read the headline totals at the top of the page.
4. Review the recent-activity list beneath the headline.
5. Click **See more...** to open the full records behind the summary.

### Expected Result

The page shows totals for exactly your chosen period with recent activity listed below. If the range has no activity, you'll see a clear message such as "No distributions found for the selected date range" instead of an empty table.

---

## Task 2: Record new activity from a report page

### Steps

1. Open the matching summary page (donations, purchases, or distributions).
2. Click the quick-create button — **New Donation**, **New Purchase**, or **New Distribution**.
3. Complete the new record as usual.

### Expected Result

You record the activity without leaving the report area, and the summary reflects it since everyday summaries always show your current records.

---

## Task 3: Check stock with the itemized reports

### Steps

1. Open an item-by-item breakdown table (itemized donations, distributions, or requests).
2. Set the date range.
3. Read each row: the item's donated, distributed, or requested amount next to what you currently have on hand.
4. Watch for cells highlighted in red in the itemized distributions and itemized requests tables.

### Expected Result

A per-item view of activity against stock. **A red cell means that item's on-hand amount has fallen below the minimum you've set — a signal to restock.**

---

## Task 4: Compare inflow and outflow with the Activity Graph

### Steps

1. Open the **Activity Graph**.
2. Set the date range.
3. Compare the bars for items received, items purchased, and items distributed.

### Expected Result

A single bar chart for the period. As a health check, received plus purchased should keep pace with distributed.

---

## Task 5: Open an NDBN Annual Report

### Steps

1. Open the annual report list. It runs from your organization's earliest reporting year through last year.
2. Note the message for the current year — it tells you the report will be "available in N months".
3. Click a completed year.

### Expected Result

The year's report opens with eight sections: Diapers; Warehouse and Storage; Adult Incontinence; Period Supplies; Other Items; Partner Agencies and Service Area; Children Served; and the Year End Summary (percentage change versus the previous year in donations, money raised, and disposable diaper donations). The first open calculates and saves the figures; later visits load instantly.

---

## Task 6: Recalculate an annual report after corrections

### Steps

1. Open the year's report.
2. Click **Recalculate Report**.

### Expected Result

The confirmation "Recalculated annual report!" appears and the figures are rebuilt from your current records. Do this whenever you've corrected past donations, purchases, or distributions for that year.

---

## Task 7: Export an annual report

### Steps

1. Open the year's report.
2. If you've corrected data since the report was last calculated, click **Recalculate Report** first — the export contains the saved figures.
3. Click **Export Report**.

### Expected Result

A CSV spreadsheet downloads, named with the report year and today's date, containing every measure from all eight sections — ready for the NDBN survey.

---

## Variations

### Year-end preparation routine

1. Correct or complete the year's records (donations, purchases, distributions, partner profiles, storage-location square footage).
2. Open the year's annual report and click **Recalculate Report**.
3. Review all eight sections, then click **Export Report** for the CSV.

### Quick restock pass

1. Open the itemized distributions table and set the range to the last few weeks.
2. List every red-highlighted item.
3. Record the needed purchases via **New Purchase** on the Purchases summary.

---

## Settings & Configuration

Reports has no settings of its own, but three kinds of upstream data shape what you see:

| Setting | Description | Default |
|---------|-------------|---------|
| Item on-hand minimums | Control the red low-stock highlighting in itemized tables | None — set per item |
| Storage-location square footage | Feeds the Warehouse and Storage section; the report flags locations missing it | Empty |
| Partner profiles | Supply agency counts, types, and zip codes served in the annual report | Per partner |

---

## Troubleshooting

### The current year is missing from the annual report list

**Cause:** Annual reports are only produced for completed years.
**Solution:** Wait for year end — the list tells you how many months remain.

### Annual report figures don't match my corrected records

**Cause:** Annual figures are frozen when first calculated; they don't update on their own (unlike the always-live daily summaries).
**Solution:** Open the year and click **Recalculate Report**, then re-export if you need a fresh CSV.

### A summary page shows a "No ... found for the selected date range" message

**Cause:** There is no activity within the chosen dates.
**Solution:** Widen or move the date range.

### Monthly averages look too low for our first year

**Cause:** Annual monthly averages always divide the year's total by twelve, even if your bank started mid-year.
**Solution:** None needed — interpret first-year monthly figures accordingly.

### Drive fundraising totals look slightly off

**Cause:** Product-drive money in the Diapers section is reported in whole dollars, so cents are dropped.
**Solution:** Expected behavior; use your purchase and donation records for cent-level accounting.
