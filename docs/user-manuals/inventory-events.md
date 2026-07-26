# Inventory Events (History) User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.

## Overview

Inventory Events provide a complete history of every inventory change in your organization. Every donation, distribution, purchase, transfer, adjustment, and kit allocation is recorded as an event. The History page lets you review these events to understand how inventory levels changed over time, troubleshoot discrepancies, and maintain an audit trail.

---

## Task 1: View Inventory Event History

### Steps

1. In the left sidebar, click **Reports** to expand the menu.
2. Click **History**.
3. The page displays a chronological list of all inventory events for your organization.

### Expected Result

You see a list of inventory events showing the event type (e.g., donation, distribution, transfer, adjustment), the date, the storage location affected, the items and quantities involved, and the user who performed the action.

---

## Task 2: Filter Inventory Events

### Steps

1. On the **History** page, use the available filters to narrow down the event list:
   - Filter by event type (donation, distribution, purchase, transfer, adjustment, kit allocation, etc.).
   - Filter by storage location.
   - Filter by date range.
2. Click the **Filter** button.
3. To remove filters, click **Clear Filters**.

### Expected Result

The event list updates to show only events matching your filter criteria, making it easier to find specific inventory changes.

---

## Task 3: Understand Event Types

### Steps

1. On the **History** page, review the event entries. Each event is labeled with its type:
   - **Donation** events show inventory increases from donations.
   - **Distribution** events show inventory decreases from distributions to partners.
   - **Purchase** events show inventory increases from purchases.
   - **Transfer** events show inventory moved between storage locations (decrease at source, increase at destination).
   - **Adjustment** events show manual inventory corrections (positive or negative).
   - **Kit allocation** events show items bundled into kits at a storage location.
   - **Kit deallocation** events show kits broken back into individual items.
   - **Snapshot** events are periodic system checkpoints for performance optimization.
2. Click on any event to see its full details if a detail view is available.

### Expected Result

You understand the meaning of each event type and can trace how a specific inventory change occurred.

---

## Task 4: Use History for Troubleshooting

### Steps

1. Navigate to the **History** page.
2. Filter by the storage location and date range in question.
3. Review the sequence of events to identify where a discrepancy may have occurred.
4. Note the event type, quantities, and user for each entry.

### Expected Result

You can trace the chain of events that led to the current inventory state and identify any unexpected changes.

---

## Variations

- **Read-only view**: The History page is a read-only audit trail. You cannot edit or delete events from this page. To correct an error, create a new adjustment.
- **Snapshot events**: The system periodically creates snapshot events to optimize performance. These are system-generated and represent a point-in-time summary of inventory, not a user action.
- **Storage location detail view**: You can also view event history for a specific storage location from the storage location detail page.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| You do not see any events on the History page. | No inventory transactions have been recorded yet, or your date filter is too narrow. | Clear all filters and check if events appear. If no events exist, perform a donation, distribution, or other inventory action first. |
| An event shows an unexpected quantity change. | A user may have entered an incorrect quantity on a transaction. | Review the specific transaction (donation, distribution, etc.) linked to the event and edit it if possible, or create an adjustment to correct the inventory. |
| You cannot find a specific event. | The event may be outside your current filter criteria. | Widen your date range and clear other filters to search more broadly. |
