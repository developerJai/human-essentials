# Transfers

## What is Transfers?

Transfers let you move inventory from one storage location to another within your organization. When you need to redistribute supplies between your warehouse, a volunteer's home, or any other storage location, a transfer records exactly what was moved, when, and between which locations.

## Key Capabilities

- Move items and quantities from one storage location to another
- Confirmation step before finalizing a transfer to prevent mistakes
- View and filter past transfers by source location, destination location, or date range
- Export transfer data to CSV
- Delete a transfer to reverse the inventory movement (with restrictions)
- Automatic inventory updates at both the source and destination locations

## How It Works

1. Navigate to Transfers and click "New Transfer."
2. Select the source storage location ("From") and the destination storage location ("To").
3. Add the items and quantities you want to move.
4. The system validates that the source location has enough of each item.
5. A confirmation screen shows a summary of what will be moved. Review and confirm.
6. The transfer is saved. Inventory is automatically decreased at the source location and increased at the destination location.
7. The transfer appears in your transfer history for future reference.

## Common Questions

**Q: Can I transfer items between organizations?**
A: No. Transfers only work between storage locations within the same organization. To send items to another organization, use a distribution.

**Q: What happens if the source location does not have enough of an item?**
A: The system checks inventory before allowing the transfer. If there is not enough of any item, the transfer is blocked and you receive an error message.

**Q: Can I edit a transfer after creating it?**
A: No. Transfers cannot be edited. If you made an error, you can delete the transfer (if allowed) or create a new transfer to move items back.

**Q: Can I delete a transfer?**
A: You can delete a transfer only if no finalized audit has occurred at either the source or destination location since the transfer was created. This restriction protects the integrity of verified inventory counts.

**Q: Does a transfer change total inventory?**
A: No. A transfer moves items from one location to another. Your organization's total inventory stays the same -- it is just distributed differently across locations.

**Q: Can I transfer to the same location?**
A: No. The source and destination must be different locations.

## Tips & Best Practices

- Always review the confirmation screen carefully before finalizing a transfer.
- Add a comment to the transfer explaining why items are being moved (for example, "Restocking main warehouse for Saturday distribution").
- Use filters on the transfer list to review movement patterns between locations.
- If you need to reverse a transfer, create a new transfer going in the opposite direction.

## Limitations & Important Notes

- Transfers cannot be edited after creation.
- Transfers cannot be deleted if a finalized audit has occurred at either location since the transfer was made.
- The source location must have enough of each item for the transfer to proceed.
- Source and destination must be different locations within the same organization.
- Each transfer draws from a single source location and sends to a single destination.

## Related Features

- **Storage Locations** -- Transfers move items between storage locations
- **Adjustments** -- For correcting inventory without moving items between locations
- **Audits** -- Finalized audits can prevent deletion of transfers
- **Inventory Events** -- Transfers create events that update inventory at both locations
- **Items** -- Transferred items come from your item catalog
