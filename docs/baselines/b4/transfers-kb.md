# Transfers

> A comprehensive guide to Transfers.

---

## What is Transfers?

Transfers move quantities of inventory from one of your storage locations to another within your organization — for example, from a warehouse to a closet or a vehicle. When a transfer is saved, the counts at both locations are updated together, and your organization's total inventory stays exactly the same; the items simply change address.

---

## Key Capabilities

- Move any number of items, each with its own quantity, between two of your storage locations in one transfer
- Enter items quickly by scanning barcodes
- Review a confirmation window listing every item and quantity before the transfer is saved
- Browse your transfer history and filter it by source location, destination location, and date range
- Download the (filtered) history as a spreadsheet with one column per item
- Delete a mistaken transfer — the inventory automatically returns to the source location

---

## How It Works

1. **Start a new transfer** — From the Transfers page, open the New Transfer form. Pick the location the items are leaving ("from") and the location receiving them ("to"). Only your organization's active storage locations are offered, and the two locations must be different.
2. **Add items and quantities** — Add one line per item with a quantity of at least 1. Use "Add Another Item" for more lines or scan barcodes. If the same item appears on two lines, the lines are merged into one with the combined quantity.
3. **Add an optional comment** — A short note stored with the transfer, shown in the history and exports.
4. **Confirm** — When you submit, the system first checks the transfer and then shows a "Transfer Confirmation" window listing every item, its quantity, and your note. Choose "No, I need to make changes" to go back, or "Yes, it's correct" to save.
5. **Done** — You return to the Transfers list with a message such as "25 items have been transferred from Main Warehouse to East Closet!" Both locations' counts are already up to date.

If you delete a transfer later, the movement is reversed and the quantities go back to the original source location.

---

## Common Questions

**Q: Can I change a transfer after it's saved?**
A: No — transfers can't be edited. The only way to correct one is to delete it (which puts the inventory back) and create a new transfer with the right details.

**Q: What happens if I try to move more than the source location holds?**
A: The transfer is rejected with a message like "location has insufficient inventory for …" naming the item(s) that fell short. Lower the quantities or restock the source location first.

**Q: Why won't the system let me delete an older transfer?**
A: If an inventory audit at either of the two locations was finalized after the transfer was made, deletion is blocked and you'll see: "We can't delete this transfer because its items were audited since you made the transfer." This protects counts that have already been verified.

**Q: Do I need a special permission to use transfers?**
A: No. Any signed-in user of your organization's account can create, view, export, and delete transfers.

**Q: Can I transfer to a location that belongs to another organization?**
A: No. Both locations must belong to your organization; anything else is rejected with "location must belong to organization".

**Q: Why is a storage location missing from the New Transfer form?**
A: Only active storage locations are offered. If a location was deactivated, it won't appear.

**Q: Why do the history filters only show some locations?**
A: The from/to filter lists include only locations that have actually been part of at least one transfer.

**Q: What does "Total Moved" mean in the list?**
A: It's the sum of the quantities of every item in that transfer.

**Q: What's in the spreadsheet download?**
A: Each transfer's From and To locations, date, comment (the word "none" when blank), and total moved — plus one column per item in your organization showing how many of that item the transfer moved (0 if it wasn't included). The file is named with the day's date, like `Transfers-2026-10-24.csv`.

---

## Tips & Best Practices

- **Use the comment field.** Transfers can't be edited, so a note like the reason for the move is the only context you can attach — and it appears in the history and exports.
- **Check the confirmation window carefully.** It shows exactly what will be saved; it's your last chance to catch a wrong quantity before inventory moves.
- **Filter before exporting.** The download matches your current filters, so narrow by location or date range first to get just the slice you need.
- **Correct mistakes before your next audit.** Once an audit of either location is finalized, the transfer can no longer be deleted — after that, fix errors with a compensating transfer or an adjustment.
- **Scan barcodes when you can.** It's faster and less error-prone than picking items from the list.

---

## Limitations & Important Notes

- Transfers cannot be edited after saving — only deleted and re-created.
- Deletion is blocked once an audit of either involved location has been finalized, even if the audit covered different items.
- Both locations must be yours and must differ from each other; every item line needs a quantity of at least 1; the source must hold enough of every item.
- A transfer with no comment shows the word "none" in the list and in the spreadsheet export.
- Transfers are internal moves: they never change your organization's overall totals.

---

## Related Features

- **Storage Locations** — the endpoints of every transfer; their inventory levels determine how much you can move.
- **Audits** — finalizing an audit locks earlier transfers at those locations against deletion, protecting verified counts.
- **Adjustments** — the right tool when a single location's count is wrong but nothing actually moved between locations.
- **Items** — transfers are built from your organization's item list, and the export shows one column per item.
