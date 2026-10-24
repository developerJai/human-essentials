# Transfers: Moving Inventory Between Storage Locations

Transfers let your bank move supplies from one storage location to another — for example, from your main warehouse to a satellite closet — while keeping your inventory counts accurate at both places automatically.

## What a transfer does

A transfer takes specific quantities of specific items out of one storage location (the "From" location) and adds them to another (the "To" location). The moment a transfer is saved, both locations' inventory levels are updated for you. Nothing enters or leaves your organization — the total amount of inventory you hold stays the same; it just changes address.

## Creating a transfer

From the Transfers page, choose **New Transfer**. You'll pick:

- **From storage location** — where the items are coming from.
- **To storage location** — where the items are going. This must be a different location than the "From" one.
- **Comment** (optional) — a note about why the transfer happened, visible later on the transfer's detail page and in exports.
- **Items in this transfer** — one or more items with quantities. You can add as many item lines as you need, and you can also enter items by scanning barcodes.

Before the transfer is saved, a confirmation window shows you exactly which items and quantities will move, along with your comment, and asks you to confirm that everything is correct. You can go back and make changes, or confirm to complete the transfer. After confirming, you'll see a message telling you how many items were transferred and between which locations.

## Rules the system enforces

- **Both locations must belong to your organization.** You can't transfer to or from anyone else's storage.
- **The two locations must be different.** A transfer from a location to itself isn't allowed.
- **You can't move more than you have.** If the "From" location doesn't hold enough of an item, the transfer is rejected and the message names the item(s) with insufficient inventory.
- **Every item line needs a quantity of at least 1.** Zero or negative quantities are rejected.
- **Duplicate item lines are merged.** If you list the same item twice, the quantities are combined into a single line automatically.

## Finding and reviewing transfers

The Transfers page lists every transfer with its From and To locations, date, comment, and the total number of items moved. You can narrow the list by:

- the location the items came **from**,
- the location the items went **to**, and
- a **date range**.

Only locations that have actually been involved in transfers appear in the filter choices. Click the view action on any row to see the full detail: each item, its quantity, the overall total, and any comment.

## Exporting transfers

When you have at least one transfer in your filtered list, an **Export Transfers** button lets you download a spreadsheet (CSV). It includes the From and To locations, date, comment, and total moved, plus one column per item in your organization showing exactly how many of that item each transfer moved. The file is named with the current date, e.g. `Transfers-2026-10-24.csv`.

## Deleting a transfer

Made a mistake? You can delete a transfer from the Transfers list (you'll be asked to confirm, since removal is permanent). Deleting a transfer automatically puts the inventory back the way it was — quantities return to the original "From" location.

**Important exception:** if either of the two locations has had an inventory audit finalized *after* the transfer was made, the transfer can no longer be deleted. The system will tell you: "We can't delete this transfer because its items were audited since you made the transfer." This protects your audited counts from being silently changed.

## Things to know

- **Transfers can't be edited.** Once saved, a transfer is fixed. To correct one, delete it (if it's still deletable) and create a new one.
- **Transfers don't change your totals.** Reports that track what comes in (donations, purchases) and goes out (distributions) aren't affected — a transfer is purely internal movement.
- **Comments are optional but useful.** They show up on the detail page and in CSV exports, so a short note like "Restock for July drive" helps later.

## Frequently asked questions

**Why can't I pick a certain storage location when creating a transfer?**
Only your organization's *active* storage locations are offered when creating a transfer. Deactivated locations don't appear.

**Why did my transfer fail with an "insufficient inventory" message?**
The From location doesn't currently hold as much of the named item(s) as you tried to move. Check the location's inventory and adjust the quantity.

**Why can't I delete an old transfer?**
An audit of one of the involved locations was finalized after that transfer. Deleting it would invalidate the audited counts, so the system blocks it.

**Does deleting a transfer delete the items?**
No. It reverses the move — the quantities go back to the From location.
