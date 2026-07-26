# Inventory Events

## What is Inventory Events?

Inventory Events is the behind-the-scenes system that tracks every change to your organization's inventory. Every donation, distribution, purchase, transfer, adjustment, and audit creates an event that records exactly what changed, when, and where. This gives your organization a complete, reliable history of all inventory movements.

## Key Capabilities

- Automatically records every inventory change as an event
- Maintains a complete history of all inventory movements
- Supports accurate inventory calculations by replaying event history
- Periodic snapshots capture a point-in-time view of all inventory for performance
- Ensures inventory totals are always consistent and auditable

## How It Works

1. Whenever you perform an inventory action (record a donation, create a distribution, make a transfer, etc.), the system automatically creates an event.
2. Each event records the items involved, the quantities, the storage location(s), and the timestamp.
3. The system calculates current inventory by processing all events in sequence.
4. Periodically, the system takes a "snapshot" of current inventory. This makes future calculations faster because the system only needs to process events since the last snapshot.
5. You do not need to interact with this system directly -- it works automatically behind the scenes.

## Common Questions

**Q: Do I need to do anything to use inventory events?**
A: No. Inventory events are created automatically whenever you perform any inventory-related action. The system handles everything behind the scenes.

**Q: What is an inventory snapshot?**
A: A snapshot is a saved copy of all inventory levels at a specific point in time. Snapshots speed up inventory calculations and serve as reference points. Once a snapshot exists, transactions that occurred before it generally cannot be edited or deleted.

**Q: Why can I not edit or delete an older donation/purchase/transfer?**
A: If an inventory snapshot was taken after that transaction, editing or deleting it would create inconsistencies. The system prevents this to protect data integrity.

**Q: How do I know if inventory events are working correctly?**
A: If your inventory totals on the dashboard and storage location pages look correct, the event system is working properly. If totals seem wrong, contact your administrator.

**Q: Can I see the event history?**
A: The event history is primarily an internal system mechanism. You can see the results of events through features like the storage location inventory view, audit history, and adjustment records.

## Tips & Best Practices

- Trust the system -- inventory events ensure your data is always consistent.
- If you notice inventory discrepancies, use an adjustment or audit to correct them rather than trying to modify old transactions.
- Understand that once a snapshot is taken, older transactions become locked. Plan corrections promptly.

## Limitations & Important Notes

- You cannot directly create, edit, or delete inventory events -- they are managed automatically.
- Transactions that occurred before an inventory snapshot cannot be modified.
- If the event history seems inconsistent, a super admin may need to take corrective action.

## Related Features

- **Donations** -- Each donation creates an inventory event
- **Distributions** -- Each distribution creates an inventory event
- **Purchases** -- Each purchase creates an inventory event
- **Transfers** -- Each transfer creates inventory events for both locations
- **Adjustments** -- Each adjustment creates an inventory event
- **Audits** -- Finalized audits create adjustment events
- **Storage Locations** -- Inventory levels are calculated from events per location
