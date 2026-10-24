# Transfers — Operations Manual

This manual is for operations staff who move inventory between storage locations: creating transfers, confirming them, reviewing past transfers, exporting records, and removing transfers made in error.

A transfer moves chosen quantities of items from one storage location (**From**) to another (**To**) within your organization. Inventory counts at both locations update automatically when the transfer is saved, and are restored automatically if the transfer is later deleted.

---

## Before you start

- You need access to your organization's inventory area in the bank portal.
- Both storage locations must already exist and be active in your organization.
- The From location must actually hold the quantities you plan to move — the system checks and will refuse a transfer that exceeds on-hand inventory.

---

## Create a transfer

1. Open the **Transfers** page (Inventory Transfers) and click **New Transfer**.
2. In **From storage location**, select where the items are coming from.
3. In **To storage location**, select where the items are going. It must be different from the From location.
4. (Optional) Enter a **Comment** describing the reason for the move.
5. Under **Items in this transfer**, select an item and enter its quantity (must be at least 1).
6. To move more than one kind of item, click **Add Another Item** and repeat. If you have barcodes, you can scan items instead of selecting them manually.
7. Click the submit button. A **Transfer Confirmation** window appears listing every item name and quantity, plus your note if you entered one.
8. Review the list carefully:
   - If something is wrong, click **No, I need to make changes** to return to the form.
   - If everything is correct, click **Yes, it's correct**.

**Result:** You return to the Transfers list with a message like "25 items have been transferred from Main Warehouse to East Closet!" Both locations' inventory counts are already updated.

### If the transfer is rejected

The form reappears with a red error message. Common causes:

| Message mentions | What it means | What to do |
|---|---|---|
| "location has insufficient inventory for …" | The From location doesn't hold enough of the named item(s) | Lower the quantity or restock the From location first |
| "location must be different than from location" | From and To are the same | Pick a different To location |
| "location must belong to organization" | A selected location isn't part of your organization | Choose locations from your own organization |
| Quantity errors | An item line has quantity 0 or blank | Enter a quantity of 1 or more on every line |

Tip: if you enter the same item on two lines, the system merges them into one line with the combined quantity — this is normal.

---

## Review transfers

1. Open the **Transfers** page. Each row shows **From**, **To**, **Date**, **Comment**, and **Total Moved**.
2. To narrow the list, use the **Transfer Filters** card:
   - **From this storage location** — only transfers out of that location.
   - **To this storage location** — only transfers into that location.
   - **Date Range** — only transfers created in that period.
3. Click **Filter** to apply, or the clear button to reset. Only locations that have been used in transfers appear in the dropdowns.
4. Click the view action on a row to open the transfer's detail page, which shows every item and quantity, the total, and any comment, under a heading like "Transfer from Main Warehouse to East Closet on 10/24/2026".

---

## Export transfers to a spreadsheet

1. On the **Transfers** page, apply any filters you want — the export respects them.
2. Click **Export Transfers** (the button appears only when the list has at least one transfer).
3. A CSV file named `Transfers-<today's date>.csv` downloads. Columns: From, To, Date, Comment (shows "none" when empty), Total Moved, then one column per item in your organization with the quantity each transfer moved (0 if the item wasn't part of that transfer).

---

## Delete a transfer

Use this when a transfer was recorded by mistake. Transfers **cannot be edited** — delete and re-create instead.

1. On the **Transfers** page, find the row.
2. Click the delete action.
3. Confirm the prompt: "Are you sure you want to permanently remove this transfer?"

**Result:** The message "Successfully deleted Transfer #<number>!" appears, and the moved quantities are returned to the original From location automatically.

### When deletion is blocked

If an inventory **audit** of either location was finalized after the transfer was made, deletion is refused with: "We can't delete this transfer because its items were audited since you made the transfer." This is intentional — removing the transfer would corrupt audited counts. If the record truly must be corrected, handle the difference with a new transfer in the opposite direction or an inventory adjustment, per your organization's audit policy.

---

## Quick reference

| Task | Where | Key control |
|---|---|---|
| Create | Transfers page | **New Transfer** |
| Confirm before saving | New Transfer form | **Yes, it's correct** |
| Filter history | Transfers page | **Transfer Filters** + **Filter** |
| View detail | Transfers list row | View action |
| Download CSV | Transfers page | **Export Transfers** |
| Remove | Transfers list row | Delete action + confirmation |

**Remember:** transfers only move inventory inside your organization — they never change your overall totals, and they can't be edited after saving.
