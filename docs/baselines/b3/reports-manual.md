# Reports — User Manual

> Step-by-step instructions for using Reports.

---

## Prerequisites

- A staff login for your organization (all reports show your organization's data only)
- Donations, purchases, and distributions recorded in the system — reports are only as good as the records behind them
- For meaningful itemized reports: on-hand minimums set on your items, so low stock is highlighted

---

## Overview

This guide is for operations staff. It covers reading the date-filtered summary reports (donations, purchases, distributions, product drives, manufacturer donations, itemized tables, and the activity graph) and the yearly workflow around the NDBN Annual Report: opening it, recalculating it after corrections, and exporting it to CSV.

---

## Task 1: Read a summary report

### Steps

1. Open the summary report you need — for example **Donations (All Sources)**, **Purchases**, or **Distributions**.
2. Set the date range in the card's filter — every figure on the card follows it.
3. Read the headline totals:
   - **Donations (All Sources)** — items received and money raised in the period
   - **Purchases** — total spent, then totals for diapers, period supplies, adult incontinence, and other, plus total items
   - **Distributions** — items distributed, plus items scheduled for future distribution
   - **Product Drives** — drives active, items received, and money raised
   - **Manufacturer Donations** — items donated and by how many manufacturers
4. Scroll to the recent-activity list (for example **Recent Donations**) and click any entry to open that record.
5. Click **See more...** at the bottom of a card to open the full list page.

### Expected Result

The card shows totals for exactly your chosen period, with clickable recent records beneath. From donation, purchase, and distribution cards you can also start a new record with **New Donation**, **New Purchase**, or **New Distribution**.

---

## Task 2: Check stock against activity (itemized reports)

### Steps

1. Open **Itemized Donations**, **Itemized Distributions**, or **Itemized Requests**.
2. Set the date range.
3. Read each row: the item, its total for the period (donated, distributed, or requested), and your current on-hand quantity. In **Itemized Requests**, an item's unit appears in parentheses when your bank uses custom units.
4. Look for on-hand cells highlighted in red — those items are below your on-hand minimum.

### Expected Result

A per-item table for the period. Red cells identify items to restock via purchase or transfer. If nothing matches the range, you'll see a notice such as "No itemized distributions found for the selected date range."

---

## Task 3: Open an NDBN Annual Report

### Steps

1. Navigate to **Reports** (breadcrumb: **Home > Reports**).
2. Note the message at the top — reports are available at the end of every year, and the page shows how many months remain for the current year.
3. In the **NDBN Annual Reports** card, click the year you need.

### Expected Result

The year's report opens with the heading "<year> NDBN Annual Report" and eight sections, each a two-column table: Diapers; Warehouse and Storage; Adult Incontinence; Period Supplies; Other Items; Partner Agencies and Service Area; Children Served; Year End Summary. The first time a year is opened the figures are calculated and saved; afterwards it opens instantly.

---

## Task 4: Recalculate an annual report

Use this after correcting or backdating donations, purchases, distributions, partner profiles, or storage locations for that year.

### Steps

1. Open the year's report (Task 3).
2. Click **Recalculate Report** near the top of the page.

### Expected Result

You return to the report with the message "Recalculated annual report!" and all eight sections recomputed from current records.

---

## Task 5: Export an annual report to CSV

### Steps

1. Open the year's report.
2. If you've made data corrections, recalculate first (Task 4).
3. Click **Export Report**.

### Expected Result

A file named `NdbnAnnuals-<year>-<today's date>.csv` downloads, containing every measure from all eight sections as labeled columns with one row of values — ready for the NDBN survey or further spreadsheet work.

---

## Variations

### Reviewing manufacturer giving before outreach

1. Open **Manufacturer Donations** and set the range to the last 12 months.
2. Note the total items and manufacturer count in the headline.
3. Use **Recent Manufacturer Donations** (your top manufacturers with donation counts) to pick outreach targets; **See more...** opens donations pre-filtered to manufacturer sources.

### Quick in-versus-out health check

1. Open **Activity Graph** and set the range.
2. Compare the three bars — items received as donations, items purchased, items distributed — to see whether inflow is keeping pace with outflow.

---

## Settings & Configuration

There are no settings pages specific to Reports, but three upstream settings shape what reports show:

| Setting | Description | Where |
|---------|-------------|-------|
| On-hand minimums | Control red low-stock highlighting in itemized reports | Item settings |
| Square footage | Feeds the Warehouse and Storage section; missing values are called out | Storage location settings |
| Partner profiles | Agency types and zip codes served in the annual report | Partner records |

---

## Troubleshooting

### The current year is missing from the annual report list

**Cause:** Annual reports cover completed years only.
**Solution:** Wait for year end — the Reports page shows how many months remain.

### Annual report figures don't reflect my corrections

**Cause:** The report is saved after its first calculation and doesn't update on its own.
**Solution:** Open the year and click **Recalculate Report**, then re-export if you need a fresh CSV.

### A summary card shows a "No ... found" message

**Cause:** Your date range has no matching records.
**Solution:** Widen or move the date range in the card's filter.

### The warehouse section mentions locations without square footage

**Cause:** Some storage locations have no square footage entered, so the total is understated.
**Solution:** Enter square footage on those storage locations, then recalculate the report.
