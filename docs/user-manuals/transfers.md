# Transfers User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least two storage locations must exist (one to transfer from, one to transfer to).
- The source storage location must have inventory to transfer.

## Overview

Transfers move inventory from one storage location to another within your organization. This is useful when you need to redistribute stock between warehouses, prepare a location for distributions, or consolidate inventory. Each transfer records the source location, destination location, the items and quantities moved, and an optional comment. A confirmation modal previews the inventory impact before saving.

---

## Task 1: View All Transfers

### Steps

1. In the left sidebar, click **Inventory** to expand the menu.
2. Click **Transfers**.
3. The page displays a table of all transfers with columns for date, from location, to location, comment, items summary, and actions.

### Expected Result

You see a paginated list of all transfers for your organization.

---

## Task 2: Filter Transfers

### Steps

1. On the **Transfers** page, use the available filters:
   - **Filter by Storage Location** to see transfers involving a specific location.
   - **Date Range** to filter by transfer date.
2. Click the **Filter** button.
3. To clear all filters, click **Clear Filters**.

### Expected Result

The transfers table updates to show only records matching your criteria.

---

## Task 3: Create a New Transfer

### Steps

1. On the **Transfers** page, click the **New Transfer** button. Alternatively, navigate to **Inventory** > **Transfers** and click the new transfer option.
2. On the **New Inventory Transfer** page, select the source from the **From storage location** dropdown.
3. Select the destination from the **To storage location** dropdown.
4. (Optional) In the **Comment** field, enter a reason for this transfer.
5. Under **Items in this transfer**, select an item from the **Item** dropdown in the first line item row.
6. Enter the **Quantity** to transfer.
7. To transfer additional items, click **Add Another Item** and repeat steps 5-6.
8. Click the **Save** button.
9. A confirmation modal appears showing the impact on inventory at both locations. Review the changes.
10. Click **Confirm** in the modal to complete the transfer.

### Expected Result

The transfer is created. Inventory at the source location decreases and inventory at the destination location increases by the transferred amounts. You are redirected to the transfer detail page.

---

## Task 4: View Transfer Details

### Steps

1. On the **Transfers** page, find the transfer you want to review.
2. Click the **View** button in the **Actions** column.

### Expected Result

The transfer detail page shows the source and destination locations, the date, the comment, and a list of all items with their transferred quantities.

---

## Task 5: Delete a Transfer

### Steps

1. On the **Transfers** page, find the transfer you want to reverse.
2. Click the **Delete** button in the **Actions** column.
3. Confirm the deletion when prompted.

### Expected Result

The transfer is removed. Inventory is restored to the source location and deducted from the destination location, reversing the original transfer.

---

## Task 6: Export Transfers to CSV

### Steps

1. On the **Transfers** page, apply any desired filters (optional).
2. Click the **Export Transfers** button.

### Expected Result

A CSV file downloads containing the filtered transfer records.

---

## Variations

- **Same-location validation**: The system prevents you from setting the same storage location as both the source and destination.
- **Confirmation modal**: The pre-submit modal shows exactly how inventory levels will change at both locations, helping you verify the transfer before committing.
- **Barcode scanning**: If barcode items are configured, scan barcodes on the transfer form to auto-add line items.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| Saving the transfer fails with an error about insufficient inventory. | The source storage location does not have enough of an item to complete the transfer. | Check inventory levels at the source location and reduce the transfer quantity or choose a different source location. |
| The **From storage location** and **To storage location** are the same. | You accidentally selected the same location for both fields. | Select different storage locations for the source and destination. |
| The confirmation modal shows unexpected changes. | The quantities you entered may differ from what you intended. | Cancel the modal, review the quantities on the form, correct them, and re-submit. |
| You cannot find the **New Transfer** button. | You may need to expand the **Inventory** menu in the sidebar. | Click **Inventory** in the sidebar, then click **Transfers** to access the transfers page where the button is available. |
