# Barcode Items User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.
- At least one item must exist in your item catalog.
- You need a barcode scanner or the barcode value to enter manually.

## Overview

Barcode Items let you link barcodes to items in your catalog so that scanning a barcode during donations, distributions, purchases, adjustments, or transfers automatically fills in the item and quantity. There are two tiers of barcodes: organization-level barcodes (specific to your bank) and global barcodes (shared across all organizations). Organization barcodes take priority over global ones when both exist for the same barcode value.

---

## Task 1: View All Barcode Items

### Steps

1. In the left sidebar, click **Inventory** to expand the menu.
2. Click **Barcode Items**.
3. The page displays a table listing all barcode-to-item mappings for your organization.

### Expected Result

You see a list of barcode items with columns showing the barcode value, associated item, quantity per barcode, and available actions.

---

## Task 2: Create a New Barcode Item

### Steps

1. Navigate to the **Barcode Items** page by clicking **Inventory** > **Barcode Items** in the left sidebar.
2. Click the **New Barcode Item** button.
3. On the new barcode item form, select the item from the **Item** dropdown that this barcode should map to.
4. In the **Barcode** field, enter the barcode value (or scan it with your barcode scanner).
5. In the **Quantity** field, enter the number of items this barcode represents (e.g., if one box contains 100 diapers, enter 100).
6. Click the **Save** button.

### Expected Result

The barcode item is created and appears in the barcode items list. When you scan this barcode on any transaction form (donation, distribution, purchase, adjustment, or transfer), the system will automatically add a line item for the associated item with the specified quantity.

---

## Task 3: Edit a Barcode Item

### Steps

1. Navigate to the **Barcode Items** page.
2. Find the barcode item you want to edit in the table.
3. Click the **Edit** button in the actions column for that barcode item.
4. Update the **Item**, **Barcode**, or **Quantity** fields as needed.
5. Click the **Save** button.

### Expected Result

The barcode item is updated with the new values. Future barcode scans will use the updated mapping.

---

## Task 4: Delete a Barcode Item

### Steps

1. Navigate to the **Barcode Items** page.
2. Find the barcode item you want to remove in the table.
3. Click the **Delete** button in the actions column for that barcode item.
4. Confirm the deletion when prompted.

### Expected Result

The barcode item is removed from the system. Scanning that barcode will no longer auto-fill item details on transaction forms.

---

## Task 5: Use a Barcode During a Transaction

### Steps

1. Navigate to any transaction form (e.g., **New Donation**, **New Distribution**, **New Purchase**, **New Adjustment**, or **New Transfer**).
2. Place your cursor in the barcode scanning area or click the barcode icon on the form.
3. Scan the barcode with your barcode scanner.
4. The system looks up the barcode and adds the corresponding item and quantity as a line item on the form.

### Expected Result

A new line item appears on the form with the item name and quantity pre-filled based on the barcode mapping. You can adjust the quantity if needed before saving.

---

## Variations

- **Organization vs. global barcodes**: Your organization's barcodes take priority. If a barcode exists at both levels, the organization-level mapping is used.
- **Multiple scans**: Scanning the same barcode multiple times adds additional line items or increments the quantity, depending on the form behavior.
- **Manual barcode entry**: If you do not have a scanner, you can type the barcode value manually into the barcode field.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| Scanning a barcode does not add a line item. | The barcode may not be registered in the system. | Go to **Inventory** > **Barcode Items** and create a new barcode item mapping for that barcode value. |
| The wrong item appears when you scan a barcode. | The barcode may be mapped to the wrong item, or a global barcode is overriding your expectation. | Edit the barcode item on the **Barcode Items** page to correct the item association. |
| You see a duplicate barcode error when creating a new barcode item. | A barcode with the same value already exists for your organization. | Search for the existing barcode item on the **Barcode Items** page and edit it instead of creating a new one. |
| The barcode scanner does not trigger input on the form. | Your scanner may not be configured to send an Enter key after scanning, or the form focus is not on the barcode capture area. | Check your scanner settings and ensure cursor focus is in the correct area of the form. |
