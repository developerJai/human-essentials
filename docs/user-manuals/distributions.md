# Distributions User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least one partner agency must exist and be approved.
- At least one storage location with inventory must exist.
- Items must be set up in your item catalog.

## Overview

Distributions are the primary way your essentials bank sends inventory out to partner agencies. Each distribution records which partner receives which items, from which storage location, on what date, and by what delivery method. You can create distributions directly or by fulfilling a partner request. The system tracks distribution status (scheduled or complete), generates PDF manifests, and can send email notifications to partners.

---

## Task 1: View All Distributions

### Steps

1. In the left sidebar, click **Distributions**.
2. The **Distributions** page displays a table with columns for **ID**, **Partner**, **Initial Allocation**, **Date of Distribution**, **Source Inventory**, **Total Items**, **Total Value**, **Delivery Method**, **Shipping Cost**, **Comments**, **Status**, and **Actions**.

### Expected Result

You see a paginated list of all distributions for your organization, with totals displayed at the bottom of the table.

---

## Task 2: Filter Distributions

### Steps

1. On the **Distributions** page, locate the **Distribution Filters** section at the top.
2. Use one or more of the following filter dropdowns:
   - **Filter by Item** to show distributions containing a specific item.
   - **Filter by Item Category** to filter by item category.
   - **Filter by Reporting Category** to filter by NDBN reporting category.
   - **Filter by Partner** to show distributions for a specific partner.
   - **Filter by Source Inventory** to filter by storage location.
   - **Filter by Status** to filter by distribution status.
   - **Date Range** to filter by a date range.
3. Click the **Filter** button.
4. To remove all filters, click **Clear Filters**.

### Expected Result

The distributions table updates to show only records matching your selected criteria. When filtering by a specific item or category, the quantity and value columns update to reflect that item or category.

---

## Task 3: Create a New Distribution

### Steps

1. On the **Distributions** page, click the **New Distribution** button in the upper-right area.
2. On the **New Distribution** page, select the receiving partner from the **Partner** dropdown.
3. Set the **Distribution date and time** using the date and time picker.
4. (Optional) Check the **Send email reminder the day before?** checkbox if you want the partner to receive a reminder.
5. (Optional) In the **Agency representative** field, enter the name of the person picking up or receiving the distribution.
6. Under **Delivery method**, select one of the available options (e.g., **Pick up**, **Delivery**, **Shipped**).
7. If you selected **Shipped**, enter the cost in the **Shipping cost** field that appears.
8. Select the source from the **Storage Location** dropdown.
9. (Optional) In the **Comment** field, add any notes about this distribution.
10. Under **Items in this distribution**, select an item from the **Item** dropdown in the first line item row.
11. Enter the quantity in the **Quantity** field.
12. To add more items, click **Add Another Item** and repeat steps 10-11.
13. Click the **Save** button.
14. If a confirmation modal appears showing the impact on inventory, review it and confirm.

### Expected Result

The distribution is created and inventory is deducted from the selected storage location. You are redirected to the distribution detail page showing a summary of the distribution.

---

## Task 4: Create a Distribution from a Partner Request

### Steps

1. In the left sidebar, click **Requests**.
2. Find the pending request you want to fulfill.
3. Click the **Start Fulfillment** button (or the action to begin fulfilling the request).
4. The **New Distribution** form opens with the partner pre-selected and requested items pre-filled.
5. Select the **Storage Location** to pull inventory from.
6. Adjust quantities if needed (you may fulfill partially).
7. Set the **Distribution date and time** and **Delivery method**.
8. Click the **Save** button.
9. Review and confirm the confirmation modal if it appears.

### Expected Result

The distribution is created, inventory is deducted, and the partner request status is updated. The partner receives a notification about the distribution.

---

## Task 5: View Distribution Details

### Steps

1. On the **Distributions** page, find the distribution you want to view.
2. Click the **View** button in the **Actions** column.

### Expected Result

The distribution detail page shows the partner, date, delivery method, storage location, all line items with quantities, total value, comments, and status.

---

## Task 6: Edit a Distribution

### Steps

1. On the **Distributions** page, find the distribution you want to edit.
2. Click the **Edit** button in the **Actions** column.
3. Update the fields as needed (date, delivery method, comment, items, quantities).
4. Click the **Save** button.

### Expected Result

The distribution is updated and inventory is adjusted accordingly. If you changed quantities, inventory at the storage location reflects the difference.

---

## Task 7: Print a Distribution PDF

### Steps

1. Navigate to the distribution detail page by clicking **View** on a distribution.
2. Click the **Print** button to generate a PDF manifest.

### Expected Result

A PDF document is generated and either downloads or opens in a new tab, showing the distribution details in a printable format suitable for packing or delivery records.

---

## Task 8: Export Distributions to CSV

### Steps

1. On the **Distributions** page, apply any desired filters (optional).
2. Click the **Export Distributions** button in the upper-right area.

### Expected Result

A CSV file downloads containing all filtered distribution records.

---

## Task 9: Reclaim a Distribution

### Steps

1. On the **Distributions** page, find the distribution you want to reclaim.
2. Click the **Reclaim** button in the **Actions** column.
3. Confirm the reclaim action when prompted.

### Expected Result

The distribution is reversed and the items are returned to inventory at the original storage location. The distribution is removed from the list.

---

## Task 10: View the Pick Ups and Deliveries Calendar

### Steps

1. In the left sidebar, click **Pick Ups & Deliveries**.
2. The calendar view shows all scheduled distributions organized by date.

### Expected Result

You see a calendar displaying upcoming distributions with their partners and scheduled dates, helping you plan logistics.

---

## Variations

- **Delivery methods**: Choose between pick up, delivery, or shipped. The shipping cost field only appears when shipped is selected.
- **Email reminders**: Enable the reminder checkbox to have the system send the partner an email one day before the scheduled distribution.
- **Partial fulfillment**: When fulfilling a request, you can adjust quantities to distribute less than what was requested.
- **Barcode scanning**: If barcode items are set up, scan barcodes on the distribution form to auto-add line items.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| You cannot select a partner on the distribution form. | No partners are approved in your organization. | Go to **Partner Agencies** > **All Partners** and ensure at least one partner has an approved status. |
| Saving the distribution fails with an inventory error. | The storage location does not have enough of an item to fulfill the distribution. | Check inventory levels at the selected storage location and reduce the quantity or choose a different location. |
| The confirmation modal shows unexpected inventory changes. | You may have entered quantities that differ from what was expected. | Review the modal carefully and adjust quantities on the form before re-submitting. |
| The **Export Distributions** button does not appear. | There are no distributions matching your current filters. | Clear your filters or create a distribution first. |
| A partner did not receive the distribution email notification. | Email notifications may not be configured, or the partner's email is incorrect. | Check the partner's email address in their profile and verify that your organization has email notifications enabled in **My Organization** settings. |
