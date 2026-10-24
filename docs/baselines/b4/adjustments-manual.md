# Inventory Adjustments — User Manual

> Step-by-step instructions for using Inventory Adjustments.

---

## Prerequisites

- You are signed in as a user of your organization — any signed-in user of the organization can view and create adjustments
- Your organization has at least one **active storage location**
- The items you need to correct exist in your organization's catalog as individual (loose), active items — kits cannot be adjusted

---

## Overview

This guide shows operations staff how to correct inventory totals at a storage location when the recorded quantity doesn't match the physical count — after miscounts, damage, loss, or typos. It covers creating an adjustment, reviewing and filtering past adjustments, exporting them to a spreadsheet, and reversing a mistaken adjustment. Adjustments are permanent records attributed to the person who made them.

---

## Task 1: Create an Adjustment

### Steps

1. Open the **Inventory Adjustments** page
2. Start a **New Adjustment**
3. Fill in the form:
   - **Storage location** — choose the location to correct; only your organization's active locations are offered, and each adjustment targets exactly one location
   - **Comment** — explain the reason for the correction; this appears in the history and in exports, so be specific
   - **Items in this adjustment** — add each item with a quantity: a positive number adds inventory, a negative number removes it
4. Click **Add Another Item** to add more lines; you can mix additions and removals in one adjustment (entering the same item twice is safe — duplicate lines are combined automatically)
5. If you have a scanner, you can enter items by barcode
6. Submit the adjustment

### Expected Result

You see the message "Adjustment was successful." and are taken to the adjustment's detail page, where each line is shown as **Added** or **Removed** with its quantity. The location's inventory totals update, and the adjustment becomes a permanent record.

If a removal exceeds the recorded stock on hand, the entire adjustment is rejected with an error and nothing is saved — reduce the removal and submit again.

---

## Task 2: Review and Filter Past Adjustments

### Steps

1. Open the **Inventory Adjustments** page — adjustments are listed newest first
2. Narrow the list using the available filters:
   - **Storage location**
   - **User** — the person who created the adjustment
   - **Date range**
3. Apply the filters
4. Open any adjustment to see its detail: each item marked **Added** or **Removed** with its quantity, plus the comment

### Expected Result

The list shows only adjustments matching your filters. Every adjustment records who created it, so you can trace any correction back to a person and a date.

---

## Task 3: Export Adjustments to a Spreadsheet

### Steps

1. On the **Inventory Adjustments** page, apply the filters for the period, location, or user you are reconciling
2. Click **Export Adjustments**

### Expected Result

A spreadsheet named `Adjustments-<today's date>.csv` downloads. It contains the created date, storage area, comment, and the number of item updates for each adjustment, followed by one column for every item your organization carries showing that adjustment's net change (0 when the item wasn't touched).

> Note: **Export Adjustments** only appears when at least one adjustment matches your current filters. If you don't see it, clear or widen the filters.

---

## Variations

### Reversing a Mistaken Adjustment

Adjustments cannot be edited or deleted. To undo one:

1. Open the mistaken adjustment and note each item and quantity
2. Create a **New Adjustment** for the same storage location
3. Enter each item with the opposite quantity (wrongly added 10 → enter -10; wrongly removed 4 → enter 4)
4. In the **Comment**, reference the original adjustment so both records tell the full story
5. Submit

Both adjustments remain in the history and the location's totals return to their correct values.

### Mixed Corrections After a Recount

When a recount finds some items over and others under, record everything in one adjustment: positive quantities for shortfalls, negative quantities for overcounts, adding lines with **Add Another Item** as you go.

---

## Settings & Configuration

Adjustments have no settings of their own. Make sure these are in place first:

| Prerequisite | Why it matters |
|---------|-------------|
| Active storage locations | An adjustment must target one active location belonging to your organization |
| Item catalog | Only your organization's individual (loose), active items can be selected — kits are excluded |

---

## Troubleshooting

### Export Adjustments is missing

**Cause:** No adjustments match the current filters; the option only appears when the list has at least one result.
**Solution:** Clear or widen the filters (for example, extend the date range) until adjustments are listed.

### My adjustment was rejected when removing items

**Cause:** A removal line exceeds the recorded stock on hand at that location; one oversized line rejects the whole adjustment and nothing is saved.
**Solution:** Check the location's current stock, lower the removal to at most what's on hand (or recount first), then submit again.

### Error: "storage location must belong to organization"

**Cause:** The chosen storage location isn't one of your organization's locations.
**Solution:** Pick a location from those offered on the form — your organization's active storage locations.

### An item I need isn't offered

**Cause:** The picker only lists your organization's individual (loose), active items; kits and inactive items don't appear.
**Solution:** Activate the item in your catalog, or handle kit quantities through the Kits feature instead of an adjustment.
