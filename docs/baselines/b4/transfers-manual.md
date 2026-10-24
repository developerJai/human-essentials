# Transfers — User Manual

> Step-by-step instructions for using Transfers.

---

## Prerequisites

- You must be signed in to your organization's account — no special permission is needed; any signed-in user of the organization can create, view, export, and delete transfers
- Your organization needs at least two active storage locations (only active locations are offered on the form)
- The source location must hold enough of every item you plan to move

---

## Overview

This guide walks you through moving inventory between two of your organization's storage locations: creating and confirming a transfer, reviewing and filtering your transfer history, downloading the history as a spreadsheet, and deleting a transfer made in error. A transfer updates the counts at both locations together and never changes your organization's overall totals. Note that transfers cannot be edited after saving.

---

## Task 1: Create a Transfer

### Steps

1. Go to the **Transfers** page and open the **New Transfer** form
2. Select the **from** location — where the items are leaving
3. Select the **to** location — where the items are going; it must be different from the from location, and both must belong to your organization
4. (Optional) Enter a **comment** — a short note stored with the transfer, shown in the history and exports
5. Add one line per item with a quantity of at least 1:
   - Click **Add Another Item** to add more lines
   - Or scan barcodes to enter items quickly
6. Submit the form — the system checks the transfer and opens the **Transfer Confirmation** window listing every item, its quantity, and your note
7. Review the list:
   - Click **No, I need to make changes** to go back to the form
   - Click **Yes, it's correct** to save the transfer

### Expected Result

You return to the Transfers list with a message such as "25 items have been transferred from Main Warehouse to East Closet!" Both locations' counts are already up to date. If you listed the same item on two lines, they were merged into one line with the combined quantity.

---

## Task 2: Review and Filter Your Transfer History

### Steps

1. Go to the **Transfers** page — the history lists each transfer with its locations, date, comment, and **Total Moved** (the sum of the quantities of every item in that transfer)
2. Narrow the list using the filters:
   - **Source location** — only transfers out of that location
   - **Destination location** — only transfers into that location
   - **Date range** — only transfers made in that period
3. Apply the filters

### Expected Result

The list shows only matching transfers. The from/to filter lists include only locations that have actually been part of at least one transfer. A transfer with no comment shows the word "none".

---

## Task 3: Download Your Transfer History

### Steps

1. On the **Transfers** page, apply any filters first — the download matches your current filters
2. Download the spreadsheet

### Expected Result

A file named with the day's date, like `Transfers-2026-10-24.csv`, downloads. It contains each transfer's From and To locations, date, comment ("none" when blank), and total moved, plus one column per item in your organization showing how many of that item the transfer moved (0 if the item wasn't included).

---

## Task 4: Delete a Transfer

Use this when a transfer was recorded by mistake. Transfers cannot be edited, so the correction path is delete, then re-create.

### Steps

1. On the **Transfers** page, find the transfer (use the filters if needed)
2. Delete it
3. Create a new transfer with the correct details if needed (see Task 1)

### Expected Result

The transfer is removed and the movement is reversed — the quantities go back to the original source location.

**If deletion is blocked:** you'll see "We can't delete this transfer because its items were audited since you made the transfer." This happens when an inventory audit at either of the two locations was finalized after the transfer was made, even if the audit covered different items. In that case, leave the record in place and fix inventory with a compensating transfer in the opposite direction, or an adjustment.

---

## Variations

### Entering items by barcode

While adding items in the New Transfer form, scan an item's barcode instead of selecting it from the list. Scanning is faster and less error-prone; adjust quantities before submitting if needed.

### Correcting a transfer before an audit

1. Delete the incorrect transfer (Task 4) — inventory returns to the source location
2. Create a new transfer with the right locations, items, and quantities (Task 1)

Do this before your next audit of either location is finalized; afterwards the transfer is locked against deletion.

---

## Settings & Configuration

Transfers have no settings of their own, but two things elsewhere control what the form offers:

| Setting | Description | Default |
|---------|-------------|---------|
| Storage location status | Only **active** storage locations appear in the from/to choices | Active |
| Item list | Transfers are built from your organization's item list; the export has one column per item | — |

---

## Troubleshooting

### The transfer is rejected with "location has insufficient inventory for …"

**Cause:** The source location doesn't hold as much of the named item(s) as you tried to move.
**Solution:** Lower the quantities, or restock the source location first, then resubmit.

### The transfer is rejected with "location must belong to organization"

**Cause:** A selected location isn't one of your organization's storage locations.
**Solution:** Choose both locations from your own organization.

### I can't delete an older transfer

**Cause:** An audit at one of the two locations was finalized after the transfer was made; deleting it would change verified counts.
**Solution:** Keep the record. Correct inventory with a compensating transfer or an adjustment.

### A storage location is missing from the New Transfer form

**Cause:** Only active storage locations are offered; the location was deactivated.
**Solution:** Reactivate the location or choose another one.

### My quantities look wrong after submitting

**Cause:** Duplicate item lines are merged automatically — two lines for the same item become one line with the combined quantity.
**Solution:** This is expected. Check the Transfer Confirmation window before saving; it shows exactly what will be recorded.
