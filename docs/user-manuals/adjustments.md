# Inventory Adjustments User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least one storage location must exist in your organization.
- At least one item must be set up in your item catalog.

## Overview

Inventory Adjustments let you manually correct inventory counts at a specific storage location. Use adjustments when physical counts differ from system records, items are damaged, or you need to account for miscellaneous gains or losses. You can increase inventory by entering a positive quantity or decrease it by entering a negative quantity. Once created, adjustments cannot be edited or deleted.

---

## Task 1: Create a New Inventory Adjustment

### Steps

1. In the left sidebar, click **Inventory** to expand the menu.
2. Click **Inventory Adjustments**.
3. On the **Inventory Adjustments** page, click the **New Adjustment** button in the upper-right area.
4. On the **New Inventory Adjustment** page, select a location from the **Storage Location** dropdown.
5. In the **Comment** field, enter a reason for this adjustment (e.g., "Physical count correction" or "Damaged items removed").
6. Under **Items in this adjustment**, select an item from the **Item** dropdown in the first line item row.
7. In the **Quantity** field, enter the amount to adjust. Enter a positive number to add inventory or a negative number (e.g., -10) to subtract inventory.
8. To adjust additional items, click **Add Another Item** and repeat steps 6-7 for each item.
9. Click the **Save** button.

### Expected Result

The system creates the adjustment and redirects you to the adjustment detail page. The inventory at the selected storage location is updated immediately. The adjustment appears in the adjustments list with the date, storage location, comment, and a summary of changes.

---

## Task 2: View All Inventory Adjustments

### Steps

1. In the left sidebar, click **Inventory** to expand the menu.
2. Click **Inventory Adjustments**.
3. The page displays a table of all adjustments with columns for **Created**, **Storage location**, **Comment**, **Summary**, and **Actions**.

### Expected Result

You see a paginated list of all inventory adjustments for your organization, sorted by date.

---

## Task 3: Filter Inventory Adjustments

### Steps

1. Navigate to the **Inventory Adjustments** page.
2. In the **Adjustment Filters** section at the top, use one or more of the following filters:
   - Select a location from the **Filter by Storage Location** dropdown.
   - Select a user from the **Filter by User** dropdown.
   - Set a **Date Range** using the date range picker.
3. Click the **Filter** button.

### Expected Result

The adjustments list updates to show only adjustments matching your filter criteria. The filters remain applied until you click **Clear Filters**.

---

## Task 4: Export Adjustments to CSV

### Steps

1. Navigate to the **Inventory Adjustments** page.
2. Apply any desired filters (optional).
3. Click the **Export Adjustments** button in the upper-right area.

### Expected Result

A CSV file downloads to your computer containing the filtered adjustment records.

---

## Task 5: View Adjustment Details

### Steps

1. Navigate to the **Inventory Adjustments** page.
2. Find the adjustment you want to view in the table.
3. Click the **View** button in the **Actions** column for that adjustment.

### Expected Result

The adjustment detail page displays the storage location, comment, date, and a list of all items and quantities that were adjusted.

---

## Variations

- **Positive adjustments**: Enter a positive number in the quantity field to add items to inventory (e.g., found items during a physical count).
- **Negative adjustments**: Enter a negative number (e.g., -5) in the quantity field to remove items from inventory (e.g., damaged or lost items).
- **Multiple items**: You can adjust multiple items in a single adjustment by clicking **Add Another Item** for each additional line.
- **Barcode scanning**: If barcode items are configured, you can scan a barcode to auto-fill the item selection on the adjustment form.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| You cannot save the adjustment and see a validation error. | You may not have selected a storage location or added at least one line item. | Ensure a **Storage Location** is selected and at least one item with a quantity is entered. |
| A negative adjustment fails or shows an error. | You may be trying to remove more items than are currently in stock at that storage location. | Check the current inventory at the storage location and enter a negative quantity that does not exceed the available stock. |
| The **Export Adjustments** button does not appear. | There are no adjustments to export. | Create at least one adjustment first, or clear your filters to see existing adjustments. |
| You cannot edit or delete a past adjustment. | Adjustments are immutable once created. | Create a new adjustment to correct the previous one (e.g., if you removed too many, create a positive adjustment to add them back). |
