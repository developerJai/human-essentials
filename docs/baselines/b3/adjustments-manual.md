# Inventory Adjustments — User Manual

> Step-by-step instructions for using Inventory Adjustments.

---

## Prerequisites

- You are signed in to your organization's bank account (any bank user can view and create adjustments for their own organization)
- At least one **active storage location** exists for your organization
- The items you want to correct exist in your organization's item catalog (individual items only — kits cannot be adjusted)

---

## Overview

This guide walks operations staff through reviewing past inventory adjustments, creating a new adjustment to correct stock counts at a storage location, reversing a mistaken adjustment, and exporting the adjustment history to a spreadsheet. Use adjustments whenever the recorded quantity of an item differs from the physical count — after recounts, damage, loss, or data-entry errors.

---

## Task 1: Create an Inventory Adjustment

### Steps

1. Navigate to **Inventory Adjustments** from your dashboard
2. Click **New Adjustment** in the top right of the filters card
3. Fill in the required fields:
   - **Storage location** — the location whose counts you are correcting; only your organization's active locations are offered
   - **Comment** — why you are adjusting (e.g., "Oct recount: 12 extra size 3"); this appears in the history and exports
   - **Items in this adjustment** — for each item, choose the item and enter a **quantity**: a plain number (e.g., `12`) adds that many; a negative number (e.g., `-5`) removes that many
4. Click **Add Another Item** to include more items in the same adjustment (you can mix additions and removals)
5. Optionally scan item barcodes to fill in item lines faster
6. Click the submit button

### Expected Result

You see the message "Adjustment was successful." and land on the adjustment's detail page, which lists each item as **Added** or **Removed** with its quantity. The storage location's inventory totals update immediately.

If something is wrong — for example a removal larger than the stock on hand, or a missing field — the form redisplays with each problem listed on its own line and nothing is saved. Fix the issues and submit again.

---

## Task 2: Review and Filter Past Adjustments

### Steps

1. Navigate to **Inventory Adjustments**
2. In the **Adjustment Filters** card, choose any of:
   - **Filter by Storage Location** — only locations that already have adjustments are listed
   - **User** — the staff member who created the adjustment
   - **Date Range** — pick a period in the date-range picker
3. Click **Filter** (or **Clear Filters** to reset)
4. Review the table: **Created**, **Storage location**, **Comment**, **Summary** (e.g., "3 changes"), **Actions**
5. Click **View** on a row to open the full detail
6. Use the pagination controls at the bottom for older records

### Expected Result

The table shows only adjustments matching your filters, newest first. The detail page shows every item change (Added/Removed with quantity), the organization, the storage location, and the comment.

---

## Task 3: Export Adjustments to a Spreadsheet

### Steps

1. Navigate to **Inventory Adjustments**
2. Apply any filters — the export includes exactly what the filtered list shows
3. Click **Export Adjustments** in the filters card footer

### Expected Result

A CSV file named `Adjustments-<today's date>.csv` downloads. Columns: **Created date**, **Storage Area**, **Comment**, **Updates** (number of item changes), followed by one column per item in your organization's catalog showing each adjustment's net change for that item (0 when untouched).

> Note: the **Export Adjustments** button only appears when at least one adjustment matches the current filters.

---

## Variations

### Reversing a Mistaken Adjustment

Adjustments cannot be edited or deleted. To undo one:

1. Open the mistaken adjustment with **View** and note each item and quantity
2. Click **New Adjustment** and select the same storage location
3. Enter each item with the opposite sign (wrongly added 10 → enter `-10`; wrongly removed 4 → enter `4`)
4. In **Comment**, reference the original adjustment and date
5. Submit

Both adjustments remain in the history, and the location's totals return to their correct values.

### Mixed Add-and-Remove Corrections

When a recount shows some items over and others under, record it all in one adjustment: enter positive quantities for the shortfalls found and negative quantities for the overcounts, using **Add Another Item** between lines. Entering the same item twice is safe — duplicate lines merge automatically.

---

## Settings & Configuration

Adjustments have no settings of their own. Two things must be configured elsewhere first:

| Prerequisite | Where | Why |
|---------|-------------|---------|
| Active storage locations | Inventory > Storage Locations | An adjustment must target one of your organization's active locations |
| Item catalog | Inventory > Items | Only your organization's active, individual (loose) items can be selected |

---

## Troubleshooting

### Export Adjustments button is missing

**Cause:** No adjustments match your current filters (the button is hidden when the list is empty).
**Solution:** Click **Clear Filters** or widen the date range until at least one adjustment is listed.

### My adjustment was rejected with an inventory error

**Cause:** One of your removals is larger than the recorded quantity on hand at that location; the whole adjustment is rejected and nothing is saved.
**Solution:**
1. Check the storage location's current stock for the item
2. Lower the removal quantity to at most the amount on hand
3. Submit again

### Error: "storage location must belong to organization"

**Cause:** The selected storage location is not one of your organization's locations.
**Solution:** Choose a location from the dropdown, which lists only your organization's active storage locations.

### An item I need isn't in the item list

**Cause:** The picker shows only your organization's individual (loose), active items — kits and deactivated items are excluded.
**Solution:** Activate the item under Inventory > Items, or manage kit quantities through the Kits feature instead.
