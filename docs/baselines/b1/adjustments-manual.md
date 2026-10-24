# Inventory Adjustments — Operations Guide

This guide is for bank staff who maintain inventory records. It covers reviewing, creating, and exporting inventory adjustments — the tool you use when the system's quantity for an item at a storage location doesn't match the physical count.

Before you start, make sure you are signed in to your organization's bank account and that the storage location you need to correct already exists and is active.

---

## 1. Review existing adjustments

1. From the dashboard, open **Inventory Adjustments**.
2. The page lists all adjustments for your organization, newest first. Columns: **Created**, **Storage location**, **Comment**, **Summary** (how many item changes), and **Actions**.
3. To narrow the list, use the **Adjustment Filters** card at the top:
   - **Filter by Storage Location** — only locations that already have adjustments are offered.
   - **User filter** — pick the staff member who created the adjustment.
   - **Date Range** — pick a period with the date-range picker.
4. Click **Filter** to apply, or **Clear Filters** to reset.
5. Click **View** on a row to open the adjustment's detail page. Each line reads **Added** or **Removed**, with the item name and quantity, plus the organization, storage location, and comment at the bottom.
6. Use the page numbers at the bottom of the list to move through older adjustments.

---

## 2. Create a new adjustment

Use this after a recount, damage, loss, or a data-entry mistake.

1. On the **Inventory Adjustments** page, click **New Adjustment** (top right of the filters card).
2. Read the on-screen reminder: an Adjustment manually increases (+) or decreases (−) inventory in one storage location.
3. Choose the **storage location** to correct. It must be one of your organization's locations.
4. Enter a **Comment** describing why you're adjusting (e.g., "Oct recount: 12 extra size 3").
5. Under **Items in this adjustment**:
   - Pick the item. Only individual (loose) items are listed — kits cannot be adjusted here.
   - Enter the **quantity**:
     - a plain number (e.g., `12`) **adds** that many;
     - a negative number (e.g., `-5`) **removes** that many.
   - Click **Add Another Item** to correct more items in the same adjustment.
   - If you have a scanner, you can capture items by barcode.
6. Click the submit button.

**Result:** you see "Adjustment was successful." and land on the adjustment's detail page. Inventory at that location updates immediately.

**If it fails:** the form redisplays with the specific errors (one per line). Common causes:

- a decrease is larger than the quantity on hand — the whole adjustment is rejected, nothing is saved;
- the storage location doesn't belong to your organization;
- a required field is missing.

Fix the listed problems and submit again.

> **Tip:** If you enter the same item twice, the two lines are automatically combined into one before saving.

---

## 3. Correct a mistaken adjustment

Adjustments cannot be edited or deleted — there is no edit button, by design, so the audit trail stays intact.

1. Open the mistaken adjustment with **View** and note each item and quantity.
2. Click back to **Inventory Adjustments** and choose **New Adjustment**.
3. Select the same storage location.
4. Enter the opposite quantities (if you wrongly added 10, enter `-10`; if you wrongly removed 4, enter `4`).
5. In the **Comment**, reference the original (e.g., "Reverses adjustment made 10/24 — wrong location").
6. Submit.

**Result:** the location's totals return to their prior values, and both records remain visible in the list.

---

## 4. Export adjustments to CSV

1. On the **Inventory Adjustments** page, apply any filters you want — the export respects the current storage-location, user, and date-range filters.
2. Click **Export Adjustments**. (The button only appears when at least one adjustment matches.)
3. A file named `Adjustments-<today's date>.csv` downloads.

Each row contains: **Created date**, **Storage Area**, **Comment**, **Updates** (number of item changes), then one column per item your organization carries showing that adjustment's net change (0 if untouched). Open it in any spreadsheet application for reconciliation or reporting.

---

## Quick reference

| Task | Where | Button |
|---|---|---|
| See all adjustments | Inventory Adjustments | — |
| Narrow the list | Filters card | **Filter** / **Clear Filters** |
| Inspect one adjustment | List row | **View** |
| Record a correction | Inventory Adjustments | **New Adjustment** |
| Undo a mistake | New Adjustment (reverse quantities) | — |
| Download a spreadsheet | Inventory Adjustments | **Export Adjustments** |

**Remember:** one adjustment = one storage location; use Transfers to move stock between locations, and Audits when you want a formal verification of physical counts.
