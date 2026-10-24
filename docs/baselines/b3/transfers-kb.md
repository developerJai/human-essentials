# Transfers

> A comprehensive guide to Transfers.

---

## What is Transfers?

Transfers let your bank move supplies from one storage location to another — say, from your main warehouse to a smaller outpost. The system updates the inventory counts at both places the moment the transfer is saved, so you never have to adjust two locations by hand. Your total inventory never changes; the items simply change address.

---

## Key Capabilities

- Move any mix of items and quantities between two of your storage locations in a single transfer
- Review a confirmation summary — every item, every quantity, your note — before anything is saved
- Browse your full transfer history and filter it by source location, destination location, and date range
- Export your (filtered) transfer history to a spreadsheet
- Delete a transfer made in error — the inventory automatically goes back where it came from

---

## How It Works

1. **Start a transfer** — From the Transfers page, choose **New Transfer** and pick the location the items are leaving and the location receiving them. The two must be different, and both must belong to your organization.
2. **Add the items** — Add one line per item with the quantity to move (at least 1 each). You can add as many lines as you like, and scan barcodes instead of typing. If you accidentally list the same item twice, the lines are merged automatically.
3. **Add a note (optional)** — A short comment, such as the reason for the move, that stays with the transfer.
4. **Confirm** — Before saving, a confirmation window shows the complete list. You can go back and make changes or confirm it's correct.
5. **Done** — You'll see a message telling you how many items moved and between which locations. Both locations' counts are already updated.

If you later delete a transfer, the system reverses the movement — the quantities return to the original source location.

---

## Common Questions

**Q: Can I edit a transfer after saving it?**
A: No. Transfers can't be changed once saved. If something is wrong, delete the transfer (which puts the inventory back) and create a new one.

**Q: What happens if I try to move more than the source location has?**
A: The transfer is rejected with a message naming the item or items that fell short. Lower the quantity or restock the source location first.

**Q: Why can't I delete an older transfer?**
A: If an inventory audit at either of the two locations was finalized after the transfer, the transfer is locked. Deleting it would silently change counts that were already audited, so the system refuses and tells you why.

**Q: Does a transfer change my organization's totals or reports?**
A: No. A transfer is purely an internal move — nothing enters or leaves your organization, so donation, purchase, and distribution figures are unaffected.

**Q: Why doesn't a particular storage location appear when creating a transfer?**
A: Only your organization's active storage locations are offered. Deactivated locations don't show up.

**Q: Why are some locations missing from the history filters?**
A: The From/To filter lists only show locations that have actually been part of at least one transfer.

**Q: Can I transfer between two locations in one step, or do I need two transfers?**
A: One step — a single transfer takes items out of the source and into the destination at the same time.

**Q: What does the "Total Moved" number mean?**
A: It's the sum of the quantities of all items in that transfer.

---

## Tips & Best Practices

- **Always use the comment field.** A note like "Monthly restock for East Closet" makes the history and exports far easier to understand later.
- **Review the confirmation window carefully.** It's your last chance to catch a wrong quantity before inventory moves — the list shown is exactly what will be saved.
- **Filter before exporting.** The spreadsheet download includes exactly the transfers matching your current filters, so narrow by location or date range first.
- **Fix mistakes promptly.** Deletion is only possible until an audit of either location is finalized — correct errors before your next audit.
- **Use barcodes for speed.** When adding items, scanning barcodes is faster and less error-prone than picking from the list.

---

## Limitations & Important Notes

- Transfers cannot be edited — only deleted and re-created.
- A transfer can't be deleted after an inventory audit of either involved location has been finalized; you'll see a message explaining this.
- Both locations must belong to your organization, must be different from each other, and the source must hold enough of every item being moved.
- Every item line needs a quantity of at least 1.
- In the history list and the spreadsheet export, a transfer with no comment shows the word "none".

---

## Related Features

- **Storage Locations** — the places transfers move inventory between; check a location's inventory before transferring from it.
- **Adjustments** — use an adjustment instead of a transfer when a single location's count is wrong but nothing actually moved.
- **Audits** — finalizing an audit locks earlier transfers at those locations against deletion, protecting verified counts.
- **Reports** — transfers are internal moves and never affect incoming or outgoing report totals.
