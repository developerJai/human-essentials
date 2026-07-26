# Purchases User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least one storage location must exist.
- At least one item must exist in your item catalog.

## Overview

Purchases record inventory that your essentials bank buys from vendors. Each purchase tracks the vendor, the items and quantities purchased, the storage location where items are stored, the total cost, cost breakdowns by product category (diapers, adult incontinence, period supplies, other), and the purchase date. Creating a purchase automatically increases inventory at the selected storage location.

---

## Task 1: View All Purchases

### Steps

1. In the left sidebar, click **Purchases** to expand the menu.
2. Click **All Purchases**.
3. The page displays a table of all purchases with columns including vendor, date, storage location, total items, total cost, and actions.

### Expected Result

You see a paginated list of all purchases for your organization.

---

## Task 2: Filter Purchases

### Steps

1. On the **Purchases** page, locate the filter section.
2. Use the available filters:
   - **Filter by Storage Location** to see purchases stored at a specific location.
   - **Filter by Vendor** to see purchases from a specific vendor.
   - **Date Range** to filter by purchase date range.
3. Click the **Filter** button.
4. To remove all filters, click **Clear Filters**.

### Expected Result

The purchases table updates to show only records matching your criteria.

---

## Task 3: Create a New Purchase

### Steps

1. In the left sidebar, click **Purchases** > **New Purchase**.
2. On the **Start a new purchase** page, select the vendor from the **Vendor** dropdown. If the vendor does not exist, click the **Add vendor** link to create one inline.
3. Select the **Storage Location** where the purchased items will be stored.
4. In the **Purchase Total** field, enter the total amount spent on this purchase.
5. (Optional) Enter category-specific cost breakdowns:
   - **Purchase Total for Diapers**
   - **Purchase Total for Adult Incontinence Products**
   - **Purchase Total for Period Supplies**
   - **Purchase Total for Other Products**
6. (Optional) In the **Comment** field, add any notes about this purchase.
7. Set the **Purchase date** using the date picker.
8. Under **Items in this purchase**, select an item from the **Item** dropdown.
9. Enter the **Quantity** for that item.
10. To add more items, click **Add Another Item** and repeat steps 8-9.
11. Click the **Save** button.

### Expected Result

The purchase is created and inventory is added to the selected storage location. You are redirected to the purchase detail page showing a summary.

---

## Task 4: View Purchase Details

### Steps

1. On the **Purchases** page, find the purchase you want to view.
2. Click the **View** button in the **Actions** column.

### Expected Result

The purchase detail page shows the vendor, date, storage location, all line items with quantities, cost breakdowns, and comments.

---

## Task 5: Edit a Purchase

### Steps

1. On the **Purchases** page, find the purchase you want to edit.
2. Click the **Edit** button in the **Actions** column.
3. Update the fields as needed (vendor, storage location, items, quantities, costs, date).
4. Click the **Save** button.

### Expected Result

The purchase is updated and inventory is adjusted to reflect any changes in items or quantities.

---

## Task 6: Delete a Purchase

### Steps

1. On the **Purchases** page, find the purchase you want to delete.
2. Click the **Delete** button in the **Actions** column.
3. Confirm the deletion when prompted.

### Expected Result

The purchase is removed and the inventory that was added by this purchase is deducted from the storage location.

---

## Task 7: Export Purchases to CSV

### Steps

1. On the **Purchases** page, apply any desired filters (optional).
2. Click the **Export Purchases** button.

### Expected Result

A CSV file downloads containing the filtered purchase records.

---

## Task 8: Create a Vendor Inline

### Steps

1. On the **New Purchase** form, if the vendor you need is not in the **Vendor** dropdown, click the **Add vendor** link.
2. In the modal that appears, enter the vendor's **Business Name** and other details.
3. Click **Save**.
4. The vendor is now available in the **Vendor** dropdown.

### Expected Result

The vendor is created without leaving the purchase form and is immediately selectable.

---

## Variations

- **Cost breakdowns**: The category-specific cost fields (diapers, adult incontinence, period supplies, other) are optional and used for the NDBN Annual Survey reporting. They do not need to add up to the Purchase Total.
- **Barcode scanning**: If barcode items are configured, scan barcodes to auto-fill line items on the purchase form.
- **Vendor management**: Vendors are managed separately under **Community** > **Vendors**, but can also be created inline from the purchase form.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| The **Vendor** dropdown is empty. | No vendors have been created yet. | Click the **Add vendor** link on the purchase form to create one, or go to **Community** > **Vendors** to add vendors. |
| Saving the purchase fails with a validation error. | Required fields may be missing (storage location, purchase total, at least one line item). | Ensure you have selected a storage location, entered a purchase total, and added at least one item with a quantity. |
| The cost breakdown fields do not add up to the Purchase Total. | The category breakdowns are optional and do not need to sum to the total. | This is expected behavior. Fill in what applies; the system does not enforce that breakdowns equal the total. |
| You cannot find a purchase you recently created. | Your filter settings may be hiding it. | Click **Clear Filters** to show all purchases. |
