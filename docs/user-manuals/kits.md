# Kits User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least two items must exist in your item catalog (kits bundle multiple items together).
- At least one storage location must exist.

## Overview

Kits let you bundle multiple items into a single reusable package. For example, a "Newborn Kit" might contain diapers, wipes, and diaper cream. Once a kit is defined, you can allocate it to storage locations (which converts the individual items into kit units) and deallocate it (which converts kit units back into individual items). Kits streamline distributions by letting you issue a single kit instead of picking individual items.

---

## Task 1: View All Kits

### Steps

1. In the left sidebar, click **Inventory** to expand the menu.
2. Click **Kits**.
3. The page displays a list of all kits with their names, component items, and actions.

### Expected Result

You see all active kits for your organization. Each kit shows what items and quantities it contains.

---

## Task 2: Create a New Kit

### Steps

1. Navigate to the **Kits** page by clicking **Inventory** > **Kits** in the left sidebar.
2. Click the **New Kit** button.
3. In the **Name** field, enter a descriptive name for the kit (e.g., "Newborn Starter Kit").
4. Under the items section, select the first item from the **Item** dropdown.
5. Enter the **Quantity** of that item to include in each kit.
6. Click **Add Another Item** to add more items to the kit.
7. Repeat steps 4-6 for each item you want to include.
8. Click the **Save** button.

### Expected Result

The kit is created and appears in the kits list. It is not yet allocated to any storage location.

---

## Task 3: Edit a Kit

### Steps

1. On the **Kits** page, find the kit you want to edit.
2. Click the **Edit** button for that kit.
3. Update the kit **Name**, items, or quantities as needed.
4. Click the **Save** button.

### Expected Result

The kit definition is updated. Note that editing a kit does not affect kits already allocated to storage locations.

---

## Task 4: Allocate a Kit to a Storage Location

### Steps

1. On the **Kits** page, find the kit you want to allocate.
2. Click the **Allocate** button for that kit.
3. Select the **Storage Location** where the kit should be assembled.
4. Enter the number of kits to allocate (the **Quantity**).
5. Click the **Save** or **Allocate** button.

### Expected Result

The system deducts the required individual items from the storage location's inventory and creates the specified number of kit units at that location. For example, if you allocate 10 "Newborn Kits" that each contain 20 diapers and 5 wipes, 200 diapers and 50 wipes are converted into 10 kit units.

---

## Task 5: Deallocate a Kit from a Storage Location

### Steps

1. On the **Kits** page or the storage location detail page, find the allocated kit.
2. Click the **Deallocate** button.
3. Select the storage location and enter the number of kits to deallocate.
4. Click the **Save** or **Deallocate** button.

### Expected Result

The kit units are broken back into their individual component items at the storage location. The kit units decrease and the individual item quantities increase accordingly.

---

## Task 6: Deactivate a Kit

### Steps

1. On the **Kits** page, find the kit you want to deactivate.
2. Click the **Deactivate** button for that kit.
3. Confirm the deactivation when prompted.

### Expected Result

The kit is marked as inactive and no longer appears in active kit lists or distribution forms. Existing allocated kit units are not affected.

---

## Task 7: Reactivate a Kit

### Steps

1. On the **Kits** page, find the inactive kit (you may need to enable a filter to show inactive kits).
2. Click the **Reactivate** button.

### Expected Result

The kit is restored to active status and becomes available for allocation and distribution again.

---

## Variations

- **Kit as a line item**: Once allocated, kits appear as selectable items on distribution forms, allowing you to distribute entire kits to partners.
- **Partial allocation**: You can only allocate as many kits as the storage location has individual items to support. If a location does not have enough of any component item, the allocation will fail.
- **Multiple locations**: You can allocate the same kit definition to different storage locations.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| Kit allocation fails with an insufficient inventory error. | The storage location does not have enough of one or more component items. | Check inventory levels at the target storage location and ensure all component items have sufficient quantity to create the requested number of kits. |
| You cannot find a kit on the distribution form. | The kit may not be allocated to the storage location selected on the distribution, or the kit is deactivated. | Allocate the kit to the correct storage location first, or reactivate the kit if it is inactive. |
| Editing a kit does not change already-allocated kits. | Kit allocations are based on the kit definition at the time of allocation. | Deallocate existing kits and reallocate them after editing the kit definition if you want the updated composition. |
| The kit appears in the items list with zero quantity. | Kits have been deallocated or no allocation has been performed. | Allocate the kit to a storage location to create kit inventory. |
