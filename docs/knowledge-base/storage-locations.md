# Storage Locations

## What is Storage Locations?

Storage Locations represent the physical places where your essentials bank stores inventory -- warehouses, closets, volunteer homes, church basements, or any other space where you keep supplies. Every item in your inventory is tracked at a specific storage location.

## Key Capabilities

- Create and manage multiple storage locations with name, address, and details
- View current inventory at each location with item-by-item detail
- View historical inventory at any past date
- Filter locations by which items they contain
- Import storage locations in bulk from a CSV file
- Import baseline inventory for new locations from a CSV file
- Export storage location data (with per-item quantities) to CSV
- Deactivate locations that are no longer in use (inventory must be zero first)
- Reactivate previously deactivated locations
- Track square footage and warehouse type for reporting

## How It Works

1. Navigate to Storage Locations from the main menu.
2. Click "New Storage Location" to add a location.
3. Enter the location name, address, and optional details (square footage, warehouse type, time zone).
4. Save the location. It is now available for use in donations, distributions, purchases, transfers, and adjustments.
5. Click on any storage location to see its current inventory -- every item and its quantity at that location.
6. Use the historical date picker to view what inventory looked like at any past date.
7. When a location is no longer in use and has zero inventory, deactivate it. Deactivated locations are hidden from dropdown menus but remain in the system for historical reference.
8. If needed, reactivate a deactivated location.

## Common Questions

**Q: Can I have items at multiple storage locations?**
A: Yes. The same item type can exist at multiple locations. Each location tracks its own quantity independently.

**Q: What happens when I deactivate a storage location?**
A: The location is hidden from dropdown menus in new transactions, but all historical records remain. You can only deactivate a location when its inventory is zero.

**Q: Can I delete a storage location?**
A: You can delete a location only if it has zero inventory. If it has any inventory, you must transfer or adjust all items out first. For locations with historical data, deactivation is recommended over deletion.

**Q: How do I import starting inventory for a new location?**
A: Use the "Import Inventory" feature. Upload a CSV file with item names and quantities. This only works for locations that have no existing inventory.

**Q: Can I see what inventory looked like on a past date?**
A: Yes. The storage location detail page has a date picker that lets you view historical inventory at any past date.

**Q: How are inventory levels calculated?**
A: The system tracks every transaction (donation, distribution, purchase, transfer, adjustment) that affects each location and calculates current inventory from that complete history.

## Tips & Best Practices

- Use clear, descriptive names for storage locations so all staff can identify them easily.
- Record the physical address accurately -- it helps with logistics and reporting.
- Use the square footage and warehouse type fields for your annual report.
- Deactivate unused locations rather than deleting them to preserve historical data.
- Export your storage location data periodically for backup and reporting.

## Limitations & Important Notes

- Deactivation requires zero inventory at the location. Transfer or adjust all items out first.
- Deleting a storage location permanently removes it and all associated transaction records (donations, distributions, transfers, adjustments, audits at that location). Use deactivation instead when possible.
- Baseline inventory import only works on locations with no existing inventory.
- Each organization manages its own storage locations independently.

## Related Features

- **Donations** -- Donated items are received at a storage location
- **Distributions** -- Items are distributed from a storage location
- **Transfers** -- Items move between storage locations
- **Adjustments** -- Manual inventory corrections happen at a specific location
- **Audits** -- Physical inventory counts are performed at a specific location
- **Items** -- Item types stored at each location
- **Inventory Events** -- All inventory changes are tracked as events per location
- **Dashboard** -- Low inventory alerts reference storage location quantities
