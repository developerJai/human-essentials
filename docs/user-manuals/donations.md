# Donations User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least one storage location must exist.
- At least one item must exist in your item catalog.
- Depending on the donation source, you may need donation sites, product drives, product drive participants, or manufacturers already set up.

## Overview

Donations record incoming inventory to your essentials bank. Each donation tracks the source (product drive, manufacturer, donation site, or miscellaneous), the items and quantities received, the storage location where they are stored, and optional details like money raised and comments. Creating a donation automatically increases inventory at the selected storage location.

---

## Task 1: View All Donations

### Steps

1. In the left sidebar, click **Donations** to expand the menu.
2. Click **All Donations**.
3. The page displays a table of all donations with columns including source, date, storage location, total items, and actions.

### Expected Result

You see a paginated list of all donations for your organization.

---

## Task 2: Filter Donations

### Steps

1. On the **Donations** page, locate the **Donation Filters** section.
2. Use one or more of the available filter dropdowns:
   - **Filter by Source** to filter by donation source type.
   - **Filter by Item** to show donations containing a specific item.
   - **Filter by Storage Location** to filter by where items were stored.
   - **Filter by Donation Site** to filter by drop-off location.
   - **Filter by Product Drive** to filter by product drive.
   - **Filter by Product Drive Participant** to filter by participant.
   - **Filter by Manufacturer** to filter by manufacturer.
   - **Date Range** to filter by a date range.
3. Click the **Filter** button.
4. To clear all filters, click **Clear Filters**.

### Expected Result

The donations table updates to show only donations matching your selected criteria.

---

## Task 3: Create a New Donation

### Steps

1. In the left sidebar, click **Donations** > **New Donation**.
2. On the **Start a new donation** page, select the donation source from the **Source** dropdown. Options include:
   - **Product Drive** - from a community donation drive
   - **Donation Site** - dropped off at a physical location
   - **Manufacturer** - donated by a manufacturer
   - **Misc. Donation** - any other source
3. Based on the source you selected, additional dropdowns appear:
   - If **Donation Site**: select the specific site from the **Donation Site** dropdown.
   - If **Product Drive**: select the drive from the **Product Drive** dropdown and optionally the **Product Drive Participant**.
   - If **Manufacturer**: select the manufacturer from the **Manufacturer** dropdown.
4. Select the **Storage Location** where the donated items will be stored.
5. (Optional) In the **Money raised in dollars** field, enter any monetary amount associated with this donation.
6. (Optional) In the **Comment** field, add any notes about this donation.
7. Set the **Issued on** date using the date picker.
8. Under **Items in this donation**, select an item from the **Item** dropdown.
9. Enter the quantity in the **Quantity** field.
10. To add more items, click **Add Another Item** and repeat steps 8-9.
11. Click the **Save** button.

### Expected Result

The donation is created and inventory is added to the selected storage location. You are redirected to the donation detail page showing a summary of the recorded donation.

---

## Task 4: View Donation Details

### Steps

1. On the **Donations** page, find the donation you want to view.
2. Click the **View** button in the **Actions** column.

### Expected Result

The donation detail page displays the source, date, storage location, all line items with quantities, money raised, comments, and a printable PDF option.

---

## Task 5: Edit a Donation

### Steps

1. On the **Donations** page, find the donation you want to edit.
2. Click the **Edit** button in the **Actions** column.
3. Update the fields as needed (source, storage location, items, quantities, comment, date).
4. Click the **Save** button.

### Expected Result

The donation is updated and inventory is adjusted to reflect the changes.

---

## Task 6: Delete a Donation

### Steps

1. On the **Donations** page, find the donation you want to delete.
2. Click the **Delete** button in the **Actions** column.
3. Confirm the deletion when prompted.

### Expected Result

The donation is removed and the inventory that was added by this donation is deducted from the storage location.

---

## Task 7: Print a Donation PDF

### Steps

1. Navigate to the donation detail page by clicking **View** on a donation.
2. Click the **Print** button.

### Expected Result

A PDF document is generated showing the donation details in a printable format for your records.

---

## Task 8: Export Donations to CSV

### Steps

1. On the **Donations** page, apply any desired filters (optional).
2. Click the **Export Donations** button.

### Expected Result

A CSV file downloads containing the filtered donation records.

---

## Task 9: Create a New Donation Site, Product Drive, or Manufacturer Inline

### Steps

1. While on the **New Donation** form, if the donation site, product drive, or manufacturer you need does not exist, click the corresponding link to add a new one (e.g., **Add product drive**, **Add manufacturer**).
2. A modal form appears where you can quickly enter the new record's details.
3. Fill in the required fields and save.
4. The new entry becomes available in the dropdown on the donation form.

### Expected Result

The new donation site, product drive participant, or manufacturer is created without leaving the donation form and is immediately selectable.

---

## Variations

- **Source-specific fields**: The form dynamically shows or hides fields based on the selected source. For example, the **Donation Site** dropdown only appears when the source is set to Donation Site.
- **Barcode scanning**: If barcode items are configured, scan barcodes to auto-fill line items on the donation form.
- **Money raised**: This is an optional field to track fundraising associated with the donation, separate from the physical items.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| You cannot select a source-specific dropdown (e.g., Donation Site is empty). | No donation sites have been created yet. | Go to **Community** > **Donation Sites** and create one, or click the inline link on the donation form to add one. |
| The **Storage Location** dropdown is empty. | No storage locations exist for your organization. | Go to **Inventory** > **Storage Locations** and create at least one storage location. |
| Saving the donation fails with a validation error. | Required fields may be missing (source, storage location, at least one line item). | Ensure you have selected a source, a storage location, and added at least one item with a quantity. |
| The donation total does not look correct after editing. | Inventory is adjusted based on the difference between old and new quantities. | Review the donation details after saving to confirm quantities are correct. If needed, create an adjustment to correct any discrepancies. |
