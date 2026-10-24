# Adjustments

> **Status**: ✅ Active
> **Generated**: 2026-10-24T00:00:00Z
> **Last Updated**: 2026-10-24T00:00:00Z
---

*Audience: customers (bank staff). This article follows the standard feature-document structure.*

## Overview

### What It Does
Inventory Adjustments let your bank manually correct the recorded quantity of items at a storage location. When the number in the system doesn't match what's on the shelf — after a recount, damage, loss, or a typo — you create an adjustment that adds or removes the difference, with a comment explaining why. Once saved, inventory totals update immediately.

### Why It Exists
Real-world counts drift from recorded counts. Adjustments keep your inventory trustworthy while preserving a permanent record of every correction: adjustments cannot be edited or deleted after they are saved, so your audit trail stays intact.

### Key Capabilities
- Correct multiple items in one adjustment, mixing additions (positive numbers) and removals (negative numbers)
- Filter the adjustments list by storage location, by the person who made it, and by date range
- View any past adjustment with each item shown as "Added" or "Removed"
- Export the (filtered) list as a spreadsheet via **Export Adjustments**
- Scan barcodes while entering items

---

## Architecture

### High-Level Design
From your point of view the flow is simple:

1. You open **Inventory Adjustments** and click **New Adjustment**
2. You choose a storage location, write a comment, and list item changes
3. The system checks your entries (valid location, enough stock for removals)
4. On success, the adjustment is saved and the location's inventory totals update

### Components
The feature is made up of the adjustments list page, the new-adjustment form (with barcode scanning support), the adjustment detail page, and a spreadsheet export.

### Technology Stack
Adjustments run inside your bank's web dashboard; no extra software, configuration, or external service is needed.

---

## Model Details

An adjustment stores, in business terms:

- **Which storage location** was corrected (it must belong to your organization)
- **Which items changed and by how much** — each line is an item plus a signed quantity; the same item entered twice is automatically combined into one line
- **Who** created the adjustment and **when**
- **A comment** explaining the reason

A positive quantity increases the recorded amount; a negative quantity decreases it.

---

## Database Schema

Each saved adjustment keeps: the date it was created, the storage location, your comment, the person who made it, and the list of item changes. These are the same fields you see on the detail page and in the export.

---

## API Endpoints

The pages you interact with:

| Where | What it does |
|-------|--------------|
| **Inventory Adjustments** list | Shows all adjustments, newest first, with filters and pagination |
| **View** (detail page) | Shows each item as Added/Removed with its quantity, plus location and comment |
| **New Adjustment** form | Creates a new correction |
| **Export Adjustments** | Downloads a CSV named `Adjustments-<today's date>.csv` |

There is deliberately no edit or delete — to fix a mistake, create a reversing adjustment.

---

## Authorization

You need to be signed in to your organization's bank account. You can only see and create adjustments for your own organization, and only against your organization's storage locations.

---

## Configuration

Nothing to configure. Storage locations must exist (and be active) before you can adjust them.

---

## Usage Examples

**Recount found extra stock:** New Adjustment → pick the location → comment "October recount: found 12 extra" → item "Diapers size 3", quantity `12` → submit. You'll see "Adjustment was successful."

**Water-damaged goods:** New Adjustment → pick the location → comment "Water damage in storeroom B" → item "Wipes", quantity `-40` → submit.

**Mixed correction:** One adjustment can both add and remove: quantity `10` on one item and `-3` on another, using **Add Another Item** between lines.

---

## Testing

Before relying on a correction, open the storage location afterwards and confirm the new totals match your physical count.

---

## Known Issues & Caveats

| Caveat | What it means for you |
|--------|----------------------|
| Adjustments are permanent | No editing or deleting; reverse a mistake with a new, opposite adjustment |
| Removals are capped by stock on hand | If a decrease exceeds what's recorded, the whole adjustment is rejected and nothing is saved |
| One location per adjustment | Use Transfers to move stock between locations |
| Loose items only | Kits can't be adjusted here |
| Export button hides when empty | **Export Adjustments** only appears when the filtered list has results |

---

## Performance

Long histories are paginated, and filters (location, user, date range) keep the list and the export manageable.

---

## Troubleshooting

### My adjustment was rejected with an inventory error
**Cause:** A removal was larger than the recorded quantity at that location.
**Solution:** Check the location's current stock and enter a smaller decrease, or recount first.

### "Storage location must belong to organization"
**Cause:** The chosen location isn't one of your organization's locations.
**Solution:** Pick a location from your own organization (the form normally only offers these).

### I can't find the Export button
**Cause:** Your current filters match no adjustments.
**Solution:** Clear or widen the filters; the button appears once at least one adjustment is listed.

---

## Related Features

- **Storage Locations** — where the corrected inventory lives
- **Transfers** — move stock between locations instead of adjusting counts
- **Audits** — formally verify physical counts
- **Items** — the catalog of things you can adjust

---

**Generated:** 2026-10-24T00:00:00Z
**Last Updated:** 2026-10-24T00:00:00Z
**Status:** ✅ Active
