# Inventory Adjustments

> A comprehensive guide to Inventory Adjustments.

---

## What is Inventory Adjustments?

Inventory Adjustments are how your bank fixes incorrect inventory totals at a storage location. When the quantity recorded in the system doesn't match what's physically on the shelf — because of miscounts, damage, loss, or typos — you create an adjustment that adds or removes the difference, along with a comment explaining why. The correction is permanent and attributed to the person who made it.

---

## Key Capabilities

- Correct several items in a single adjustment, mixing additions (positive quantities) and removals (negative quantities)
- Target exactly one storage location per adjustment, chosen from your organization's active locations
- Browse your organization's adjustments newest-first, filtered by storage location, by the person who created them, and by date range
- Open any adjustment to see each line shown as Added or Removed with its quantity
- Export the filtered list as a spreadsheet named `Adjustments-<today's date>.csv`
- Enter items by barcode on the creation form

---

## How It Works

1. **Open the list** — the Inventory Adjustments page shows every adjustment your organization has made, newest first, with filters for storage location, user, and date range.
2. **Start a new adjustment** — use the **New Adjustment** form. Pick one of your organization's active storage locations and write a comment explaining the reason for the correction.
3. **Add item lines** — under "Items in this adjustment", list each item with a quantity. Positive numbers add inventory; negative numbers remove it. Click **Add Another Item** for more lines; duplicate lines for the same item are combined automatically before saving. Only individual (loose) items are offered — kits are excluded.
4. **Submit** — the system verifies that the storage location belongs to your organization and that removals don't exceed what's on hand. If any line would remove more than the recorded stock, the entire adjustment is rejected and nothing is saved.
5. **Confirmation** — on success you see "Adjustment was successful." and are taken to the adjustment's detail page. The inventory totals at that location update, and the adjustment becomes a permanent record that cannot be edited or deleted.

---

## Common Questions

**Q: Can I change or delete an adjustment after saving it?**
A: No. Adjustments are immutable once created — there is deliberately no edit or delete. To fix a mistake, create a new adjustment with the opposite quantities.

**Q: What happens if I try to remove more of an item than the location has?**
A: The adjustment is rejected with an error message and nothing is saved. Reduce the removal to at most the quantity on hand, or recount first.

**Q: Can one adjustment span two storage locations?**
A: No — every adjustment targets exactly one storage location. Use a Transfer to move stock between locations.

**Q: What if I enter the same item twice?**
A: Duplicate lines are automatically combined into one before the adjustment is saved.

**Q: Can I adjust kits?**
A: No. Only individual (loose), active items from your organization's catalog appear in the item picker.

**Q: Who can create adjustments?**
A: Any signed-in user of your organization. You only ever see and create adjustments for your own organization, and every adjustment records who created it.

**Q: What does the error "storage location must belong to organization" mean?**
A: The chosen storage location isn't one of your organization's locations. Pick a location from the ones the form offers — your organization's active locations.

**Q: How do I get a report of adjustments?**
A: Filter the list as needed and use **Export Adjustments**. The spreadsheet contains the created date, storage area, comment, the number of item updates, and one column for every item your organization carries showing each adjustment's net change (0 when untouched).

---

## Tips & Best Practices

- Write a specific comment every time — it appears in the history and the export, and it's the only explanation future staff will have.
- Check the location's current stock before entering removals so the adjustment isn't rejected for exceeding what's on hand.
- Combine all corrections for one location into a single adjustment; you can mix additions and removals freely.
- Filter by date range or location before exporting so the spreadsheet matches exactly the period you're reconciling.
- To undo a mistake, create a reversing adjustment (opposite quantities) and mention the original in the comment — both records stay in the history.

---

## Limitations & Important Notes

- Adjustments cannot be edited or deleted after saving; corrections are made with new, reversing adjustments.
- One storage location per adjustment.
- Removals cannot exceed recorded stock; a single oversized line rejects the whole adjustment.
- Kits can't be adjusted — loose items only.
- The **Export Adjustments** option only appears when at least one adjustment matches the current filters.
- The storage location must be an active location belonging to your organization.

---

## Related Features

- **Storage Locations** — every adjustment corrects inventory at one of your storage locations.
- **Transfers** — the right tool when stock physically moved between two locations.
- **Audits** — formal physical-count verification that often leads to adjustments.
- **Items** — the catalog of loose items available for adjustment.
