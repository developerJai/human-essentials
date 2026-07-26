# Storage Locations User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.

## Overview

Storage Locations represent the physical places where your essentials bank stores inventory (e.g., warehouses, closets, partner offices). Every inventory transaction (donation, distribution, purchase, transfer, adjustment) references a storage location. The system tracks current inventory levels at each location using event-sourced data, and provides tools to view, filter, import, export, and manage these locations.

---

## Task 1: View All Storage Locations

### Steps

1. In the left sidebar, click **Inventory** to expand the menu.
2. Click **Storage Locations**.
3. The page displays a table of all storage locations with columns for **Name**, **Address**, **Square Footage**, **Warehouse Type**, **Total Inventory**, **Fair Market Value**, and **Actions**.
4. A totals row at the bottom shows aggregate inventory and value.

### Expected Result

You see all active storage locations with their current inventory counts and values.

---

## Task 2: Filter Storage Locations

### Steps

1. On the **Storage Locations** page, locate the **Storage Location Filters** section.
2. Select an item from the **Filter by Item** dropdown to see only locations that contain that item.
3. (Optional) Check the **include inactive storage locations** checkbox to see deactivated locations.
4. Click the **Filter** button.
5. To clear filters, click **Clear Filters**.

### Expected Result

The storage locations table updates to show only locations matching your criteria.

---

## Task 3: Create a New Storage Location

### Steps

1. Navigate to the **Storage Locations** page.
2. Click the **New Storage Location** button in the upper-right area.
3. In the **Name** field, enter a descriptive name (e.g., "Main Warehouse" or "Community Center Closet").
4. In the **Address** field, enter the physical address.
5. (Optional) Enter the **Square Footage**.
6. (Optional) Select the **Warehouse Type**.
7. Click the **Save** button.

### Expected Result

The storage location is created and appears in the list. It is now available for selection on donation, distribution, purchase, transfer, and adjustment forms.

---

## Task 4: View Storage Location Details and Inventory

### Steps

1. On the **Storage Locations** page, find the location you want to inspect.
2. Click the **View** button in the **Actions** column.
3. The detail page shows the location's name, address, and a complete list of items currently in stock at that location with quantities.

### Expected Result

You see a detailed inventory breakdown for the selected storage location, showing every item and its current quantity.

---

## Task 5: Edit a Storage Location

### Steps

1. On the **Storage Locations** page, find the location you want to edit.
2. Click the **Edit** button in the **Actions** column.
3. Update the **Name**, **Address**, **Square Footage**, or **Warehouse Type** as needed.
4. Click the **Save** button.

### Expected Result

The storage location information is updated.

---

## Task 6: Deactivate a Storage Location

### Steps

1. On the **Storage Locations** page, find the location you want to deactivate.
2. Click the **Deactivate** button in the **Actions** column.
3. Confirm the deactivation when prompted.

### Expected Result

The storage location is marked as inactive. It no longer appears as an option on transaction forms, but existing records referencing it are preserved. Inventory at this location remains recorded but cannot receive new transactions.

---

## Task 7: Reactivate a Storage Location

### Steps

1. On the **Storage Locations** page, check the **include inactive storage locations** checkbox and click **Filter**.
2. Find the deactivated location in the list.
3. Click the **Reactivate** button in the **Actions** column.

### Expected Result

The storage location is restored to active status and reappears on transaction form dropdowns.

---

## Task 8: Import Storage Locations from CSV

### Steps

1. Navigate to the **Storage Locations** page.
2. Click the **Import Storage Locations** button (this button appears when no storage locations exist yet).
3. In the CSV import modal, download the template by clicking the template link.
4. Open the template in a spreadsheet program, delete the sample data, and enter your storage location names and addresses in the appropriate columns.
5. Save the file as a CSV file.
6. Back in the import modal, click **Choose File** and select your CSV file.
7. Click **Upload** to import the locations.

### Expected Result

Storage locations from your CSV file are created in the system and appear in the list.

---

## Task 9: Export Storage Locations to CSV

### Steps

1. On the **Storage Locations** page, apply any desired filters.
2. Click the **Export Storage Locations** button.

### Expected Result

A CSV file downloads containing your storage location data and inventory information.

---

## Task 10: View Historical Inventory at a Storage Location

### Steps

1. Navigate to the storage location detail page by clicking **View** on a location.
2. Look for a historical inventory or event history section on the detail page.
3. Review the timeline of inventory changes at this location.

### Expected Result

You see a history of all inventory events (donations, distributions, transfers, adjustments) that affected this storage location, allowing you to trace how inventory levels changed over time.

---

## Variations

- **Geocoding**: If an address is provided, the system may geocode it for use in the Distributions by County report and mapping features.
- **Square footage and warehouse type**: These optional fields help track the physical capacity and type of each storage space.
- **Fair market value**: The system calculates the total fair market value of inventory at each location based on item values.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| A storage location does not appear in the dropdown when creating a transaction. | The location may be deactivated. | Go to **Inventory** > **Storage Locations**, check the **include inactive storage locations** filter, find the location, and reactivate it. |
| Inventory counts at a location do not match physical counts. | Transactions may not have been recorded or errors occurred. | Use the **History** report to review all events at the location. Create an adjustment to correct any discrepancies. |
| CSV import fails. | The CSV file may not match the expected template format. | Download the template again, match column headers exactly, and re-upload. |
| The **Import Storage Locations** button is not visible. | The button only appears when no storage locations exist. | If you already have locations, create new ones individually using the **New Storage Location** button. |
