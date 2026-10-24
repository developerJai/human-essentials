# Transfers — User Manual

> Step-by-step instructions for using Transfers.

---

## Prerequisites

- You must be signed in as a user of your organization's bank account (no extra transfer-specific permission is needed)
- At least two active storage locations must exist in your organization
- The source location must hold the items and quantities you plan to move
- Items you want to transfer must be active in your organization's item list

---

## Overview

This guide walks operations staff through the full transfer workflow: creating an inventory transfer between two storage locations, confirming it, reviewing and filtering past transfers, exporting the history to a spreadsheet, and deleting a transfer made in error. Transfers update the inventory counts at both locations automatically and cannot be edited after saving.

---

## Task 1: Create a Transfer

### Steps

1. Navigate to the **Transfers** page (Inventory Transfers)
2. Click **New Transfer** in the filter card's footer (top area of the page, right side)
3. Fill in the form:
   - **From storage location** — where the items are coming from ("Which location are you moving inventory from?")
   - **To storage location** — the location receiving the items; must be different from the From location
   - **Comment** — optional note about the move (e.g., reason or reference)
4. Under **Items in this transfer**, select an item and enter its quantity (minimum 1)
5. Click **Add Another Item** to add more lines as needed; you can also scan barcodes to add items
6. Click the submit button — a **Transfer Confirmation** window opens listing every item name and quantity, plus your note if you entered one
7. Check the list:
   - Click **No, I need to make changes** to return to the form, or
   - Click **Yes, it's correct** to save the transfer

### Expected Result

You are returned to the Transfers list with a message like "25 items have been transferred from Main Warehouse to East Closet!" Inventory at both locations is already updated. If the same item appeared on two lines, they are merged into one line with the combined quantity.

---

## Task 2: Review and Filter Transfer History

### Steps

1. Navigate to the **Transfers** page — the table shows **From**, **To**, **Date**, **Comment**, and **Total Moved** for each transfer
2. In the **Transfer Filters** card, set any of:
   - **From this storage location** — show only transfers out of that location
   - **To this storage location** — show only transfers into that location
   - **Date Range** — show only transfers created within the range
3. Click **Filter** (use the clear button to reset)
4. Click the view action on a row to open the transfer's detail page

### Expected Result

The list narrows to matching transfers. The detail page is titled like "Transfer from Main Warehouse to East Closet on 10/24/2026" and lists each item with its quantity, a **Total** row, and a **Comments** row when a note was entered. Note: the filter dropdowns only offer locations that have been part of at least one transfer.

---

## Task 3: Export Transfers to a Spreadsheet

### Steps

1. On the **Transfers** page, apply any filters you want included — the export matches the filtered list
2. Click **Export Transfers** (shown only when the list contains at least one transfer)

### Expected Result

A file named `Transfers-<today's date>.csv` downloads. It contains columns for From, To, Date, Comment (the word "none" when empty), and Total Moved, followed by one column per item in your organization showing the quantity of that item each transfer moved (0 when the item wasn't included).

---

## Task 4: Delete a Transfer

### Steps

1. On the **Transfers** page, locate the transfer (use filters if needed)
2. Click the delete action on its row
3. Confirm the prompt: "Are you sure you want to permanently remove this transfer?"

### Expected Result

The message "Successfully deleted Transfer #<number>!" appears and the moved quantities are automatically returned to the original From location. If an audit of either location was finalized after the transfer, deletion is refused with "We can't delete this transfer because its items were audited since you made the transfer."

---

## Variations

### Adding items by barcode

When filling the **Items in this transfer** section, scan an item's barcode instead of selecting it from the dropdown. The scanned item and its barcode quantity are added as a line; adjust the quantity if needed before submitting.

### Correcting a saved transfer

Transfers cannot be edited. To fix a mistake:

1. Delete the incorrect transfer (Task 4) — this restores the inventory
2. Create a new transfer with the correct details (Task 1)

If deletion is blocked by a finalized audit, instead create a compensating transfer in the opposite direction, or use an inventory adjustment, per your organization's audit policy.

---

## Settings & Configuration

Transfers have no settings page of their own. What appears in the form is controlled elsewhere:

| What | Where it's managed | Effect on transfers |
|------|--------------------|---------------------|
| Storage locations | Storage Locations area | Only **active** locations appear in the From/To dropdowns |
| Items | Items area | Only **active** items are offered when creating a transfer |

---

## Troubleshooting

### The transfer is rejected with "location has insufficient inventory for …"

**Cause:** The From location holds fewer of the named item(s) than the quantity you entered.
**Solution:** Lower the quantity, or move stock into the From location first, then resubmit.

### The transfer is rejected with "location must be different than from location"

**Cause:** The same storage location is selected as both From and To.
**Solution:** Choose a different To location.

### Delete fails with "We can't delete this transfer because its items were audited since you made the transfer."

**Cause:** An inventory audit covering one of the two locations was finalized after this transfer was created; removing it would invalidate the audited counts.
**Solution:** Leave the transfer in place. Correct inventory with a reverse transfer or an adjustment instead.

### The Export Transfers button is missing

**Cause:** The current (filtered) list contains no transfers.
**Solution:** Clear or widen the filters so at least one transfer is listed.

### A storage location doesn't appear in the New Transfer dropdowns

**Cause:** The location is deactivated.
**Solution:** Reactivate it under Storage Locations, or pick a different location.
