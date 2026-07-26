# Requests User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least one partner agency must be approved and able to submit requests.
- At least one storage location with inventory must exist for fulfillment.

## Overview

Requests are supply orders submitted by partner agencies through the partner portal. As bank staff, you manage requests by reviewing them, starting fulfillment, creating distributions to fulfill them, and tracking their status. Requests move through a lifecycle: Pending, Started, Fulfilled, or Discarded. You can also view a picklist PDF to help with order picking and export requests to CSV.

---

## Task 1: View All Requests

### Steps

1. In the left sidebar, click **Requests**.
2. The page displays a table of all requests with columns for partner name, date, status, items requested, and actions.

### Expected Result

You see a paginated list of all partner requests for your organization, with their current statuses.

---

## Task 2: Filter Requests

### Steps

1. On the **Requests** page, use the available filters:
   - **Filter by Partner** to see requests from a specific partner.
   - **Filter by Status** to see requests in a specific state (Pending, Started, Fulfilled, Discarded).
   - **Filter by Item** to find requests containing a specific item.
   - **Date Range** to filter by request date.
2. Click the **Filter** button.
3. To clear all filters, click **Clear Filters**.

### Expected Result

The requests table updates to show only requests matching your criteria.

---

## Task 3: View Request Details

### Steps

1. On the **Requests** page, find the request you want to review.
2. Click the **View** button in the actions column.

### Expected Result

The request detail page shows the partner name, request date, status, all requested items with quantities, and any comments.

---

## Task 4: Start Fulfilling a Request

### Steps

1. On the **Requests** page, find a request with **Pending** status.
2. Click the **Start Fulfillment** button in the actions column.
3. You are taken to the **New Distribution** form with the partner pre-selected and the requested items pre-filled.
4. Select the **Storage Location** to pull inventory from.
5. Adjust quantities if needed (you may fulfill partially or fully).
6. Set the **Distribution date and time** and **Delivery method**.
7. Click the **Save** button.
8. Confirm the distribution in the confirmation modal if it appears.

### Expected Result

A distribution is created, inventory is deducted from the storage location, and the request status changes to "Fulfilled." The partner receives a notification about the completed distribution.

---

## Task 5: Discard a Request

### Steps

1. On the **Requests** page, find the request you want to cancel.
2. Click the **Discard** button in the actions column.
3. Confirm the action when prompted.

### Expected Result

The request status changes to "Discarded." No distribution is created and no inventory is affected.

---

## Task 6: Generate a Picklist PDF

### Steps

1. On the **Requests** page, find the request you want to pick.
2. Click the **Picklist** button or link.

### Expected Result

A PDF document is generated listing all items and quantities needed for the request, organized for efficient picking from your storage locations. You can print this document and use it in your warehouse.

---

## Task 7: Export Requests to CSV

### Steps

1. On the **Requests** page, apply any desired filters (optional).
2. Click the **Export Requests** button.

### Expected Result

A CSV file downloads containing the filtered request records.

---

## Task 8: Monitor Requests from the Dashboard

### Steps

1. Navigate to the **Dashboard** by clicking **Dashboard** in the left sidebar.
2. Check the pending requests count displayed on the dashboard.
3. Click the notification bell icon in the top navigation bar to see a quick summary of pending requests.
4. Click the **Requests** link in the notification dropdown to go directly to the requests page.

### Expected Result

You can quickly see how many requests need attention without navigating to the full requests page.

---

## Variations

- **Partial fulfillment**: When starting fulfillment, you can adjust the quantities to distribute fewer items than requested. The request will still be marked as fulfilled when the distribution is saved.
- **Multiple request types**: Partners may submit quantity-based, individual, or child/family-based requests depending on your bank's configuration. All types appear in the same requests list.
- **Custom units (packs)**: If your bank uses the packs feature, requested quantities may be shown in custom units alongside total units.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| No requests appear on the page. | There may be no pending requests, or your filters may be hiding them. | Click **Clear Filters** and check all statuses. If no requests exist, partners need to submit them through the partner portal. |
| You cannot start fulfillment on a request. | The request may already be started, fulfilled, or discarded. | Check the request's status. Only **Pending** requests can have fulfillment started. |
| The distribution form shows different items than the request. | The request may contain items that are unavailable or deactivated. | Review the request details and the distribution form carefully. Adjust items on the distribution form as needed. |
| The partner did not receive a notification after fulfillment. | Email notifications may not be configured for your organization. | Check your organization's email settings under **My Organization** to ensure notifications are enabled. |
