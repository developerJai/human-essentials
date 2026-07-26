# Barcode Items

## What is Barcode Items?

Barcode Items lets you link product barcodes to items in your catalog. When you scan a barcode during donations, purchases, or other inventory activities, the system automatically identifies the item and fills in the quantity, saving time and reducing errors.

## Key Capabilities

- Create barcode-to-item mappings for your organization
- Scan barcodes to quickly add items during data entry
- Set a default quantity per barcode (for example, one barcode scan could represent a pack of 24)
- Two levels of barcodes: organization-specific barcodes and global barcodes shared across all organizations
- View and manage all your organization's barcode mappings

## How It Works

1. Navigate to Barcode Items from the main menu.
2. Click "New Barcode" to create a mapping.
3. Enter the barcode value (the number from the product's UPC or other barcode).
4. Select which item in your catalog this barcode represents.
5. Enter the quantity that one scan of this barcode should add (for example, 24 if it is a case pack).
6. Save the barcode mapping.
7. Now, when entering donations, purchases, or other transactions, you can scan this barcode and the system will automatically fill in the item and quantity.

## Common Questions

**Q: What is the difference between an organization barcode and a global barcode?**
A: Organization barcodes are specific to your essentials bank. Global barcodes are set up by super admins and work for all organizations on the platform. If both exist for the same barcode value, your organization's mapping takes priority.

**Q: Can I set a quantity per barcode?**
A: Yes. When creating a barcode mapping, you specify how many units one scan represents. For example, if a barcode is on a case of 24 diapers, you can set the quantity to 24.

**Q: What if I scan a barcode that is not in the system?**
A: The system will not recognize it. You will need to create a barcode mapping first, or enter the item manually.

**Q: Can I change a barcode mapping after creating it?**
A: Yes. You can edit the item or quantity associated with a barcode at any time.

**Q: Who can manage global barcodes?**
A: Only super admins can create or edit global barcodes through the Admin Panel. Organization users manage their own organization-level barcodes.

## Tips & Best Practices

- Set up barcode mappings for your most commonly received items to speed up data entry.
- Use the correct quantity per barcode to match how items are packaged (individual, pack, case).
- Check for existing global barcodes before creating organization-specific ones -- the item may already be mapped.

## Limitations & Important Notes

- Barcode scanning requires the barcode value to already be mapped in the system.
- If a product changes its packaging or barcode, you will need to update the mapping.
- Global barcodes can only be managed by super admins, not by organization users.

## Related Features

- **Items** -- Barcodes link to items in your catalog
- **Donations** -- Barcode scanning can be used when recording donations
- **Purchases** -- Barcode scanning can be used when recording purchases
- **Admin Panel** -- Super admins manage global barcodes here
