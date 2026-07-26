# Items & Inventory User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.

## Overview

Items represent the types of products your essentials bank manages (e.g., diapers size 3, period pads, wipes). The Items & Inventory page is the central hub for managing your item catalog, item categories, and reviewing inventory levels across storage locations. Items can be organized by categories, assigned NDBN reporting categories, given custom request units, and deactivated when no longer in use.

---

## Task 1: View the Item List

### Steps

1. In the left sidebar, click **Inventory** to expand the menu.
2. Click **Items & Inventory**.
3. On the Items & Inventory page, ensure the **Item List** tab is selected (it is active by default).
4. The table shows all active items with their names, categories, and other details.

### Expected Result

You see a list of all active items in your catalog. Use the tabs at the top to switch between different views.

---

## Task 2: Filter Items

### Steps

1. On the **Items & Inventory** page, locate the **Item Filter** section.
2. Select a category from the **Filter by NDBN Reporting Category** dropdown.
3. (Optional) Check the **Also include inactive items** checkbox to see deactivated items.
4. Click the **Filter** button.
5. To clear filters, click **Clear Filters**.

### Expected Result

The item list updates to show only items matching your filter criteria.

---

## Task 3: Create a New Item

### Steps

1. On the **Items & Inventory** page under the **Item List** tab, click the **New Item** button (or the add button near the item list).
2. In the item form, enter the **Name** for the new item (e.g., "Diapers - Size 4").
3. Select an **Item Category** from the dropdown (or leave blank if categories are not in use).
4. Select the **NDBN Reporting Category** that best describes this item for reporting purposes.
5. (Optional) Set the **Minimum Quantity** threshold for low inventory alerts.
6. (Optional) Set the **Fair Market Value** per unit for reporting.
7. (Optional) Configure **Custom Request Units** if your organization uses the packs feature (e.g., "pack of 50").
8. Click the **Save** button.

### Expected Result

The new item is created and appears in the item list. It is now available for use in donations, distributions, purchases, adjustments, and transfers.

---

## Task 4: Edit an Item

### Steps

1. On the **Items & Inventory** page, find the item you want to edit in the **Item List** tab.
2. Click the **Edit** button for that item.
3. Update the fields as needed (name, category, reporting category, minimum quantity, value).
4. Click the **Save** button.

### Expected Result

The item is updated with the new details.

---

## Task 5: Deactivate an Item

### Steps

1. On the **Items & Inventory** page, find the item you want to deactivate in the **Item List** tab.
2. Click the **Deactivate** button for that item.
3. Confirm the deactivation when prompted.

### Expected Result

The item is marked as inactive. It no longer appears in dropdowns on transaction forms (donations, distributions, etc.), but historical records that reference it are preserved. To see inactive items, check the **Also include inactive items** filter checkbox.

---

## Task 6: Reactivate an Item

### Steps

1. On the **Items & Inventory** page, check the **Also include inactive items** checkbox in the filter section and click **Filter**.
2. Find the inactive item in the list.
3. Click the **Reactivate** button for that item.

### Expected Result

The item is restored to active status and reappears in transaction form dropdowns.

---

## Task 7: Manage Item Categories

### Steps

1. On the **Items & Inventory** page, click the **Item Categories** tab.
2. The table shows all item categories for your organization.
3. To create a new category, click the **New Category** button, enter a **Name** and optional **Description**, and click **Save**.
4. To edit a category, click the **Edit** button next to it, make changes, and click **Save**.
5. To delete a category, click the **Delete** button and confirm.

### Expected Result

Item categories are managed and can be assigned to items for grouping and filtering purposes.

---

## Task 8: View Items, Quantity, and Location

### Steps

1. On the **Items & Inventory** page, click the **Items, Quantity, and Location** tab.
2. This view shows each item with its current quantity broken down by storage location.

### Expected Result

You see a matrix of items and storage locations with inventory quantities, providing a comprehensive overview of where your inventory is stored.

---

## Task 9: View Item Inventory

### Steps

1. On the **Items & Inventory** page, click the **Item Inventory** tab.
2. This view shows total inventory counts per item across all storage locations.

### Expected Result

You see the total quantity of each item in your organization, regardless of which storage location holds it.

---

## Task 10: View Kits from the Items Page

### Steps

1. On the **Items & Inventory** page, click the **Kits** tab.
2. This tab shows all active kits and their component items.

### Expected Result

You see a list of kits with their contents, providing a quick reference without navigating to the dedicated Kits page.

---

## Task 11: Export Items to CSV

### Steps

1. On the **Items & Inventory** page, apply any desired filters.
2. Click the **Export Items** button.

### Expected Result

A CSV file downloads containing your item catalog data.

---

## Variations

- **Custom request units (packs)**: If your organization has the packs feature enabled, you can define custom units (e.g., "pack of 24") for items. Partners can then request in these units.
- **NDBN reporting categories**: These standardized categories are used for the NDBN Annual Survey. Each item should be assigned the appropriate reporting category.
- **Minimum quantity alerts**: Items with a minimum quantity set will appear on the dashboard low inventory alerts when stock falls below that threshold.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| An item does not appear in the dropdown when creating a donation or distribution. | The item may be deactivated. | Go to **Inventory** > **Items & Inventory**, check the **Also include inactive items** filter, find the item, and reactivate it. |
| You cannot delete an item. | Items that have been used in transactions cannot be deleted. | Deactivate the item instead. This preserves historical records while preventing future use. |
| Item quantities do not match expected values. | Transactions may not have been recorded or an error occurred. | Check the **History** page under **Reports** to review all inventory events for that item. |
| The **Kits** tab shows no kits. | No kits have been created yet. | Go to **Inventory** > **Kits** to create kits. |
