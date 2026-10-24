# Adjustments

> **Status**: ✅ Active
> **Generated**: 2026-10-24T00:00:00Z
> **Last Updated**: 2026-10-24T00:00:00Z
---

*Audience: operations staff. This manual follows the standard feature-document structure.*

## Overview

### What It Does
Inventory Adjustments are your tool for fixing the recorded quantity of items at a storage location when it doesn't match the physical count. You record which items to add or remove, at which location, and why; the system updates inventory totals as soon as the adjustment saves.

### Why It Exists
Operations teams routinely find discrepancies after recounts, spoilage, damage, or data-entry mistakes. Adjustments correct the record while keeping a permanent, attributable history — saved adjustments can never be edited or deleted.

### Key Capabilities
- Correct several items in one go, adding (positive quantity) and removing (negative quantity) in the same adjustment
- Filter history by storage location, user, and date range
- Inspect any adjustment's detail (Added/Removed per item)
- Download the filtered history as `Adjustments-<date>.csv` with **Export Adjustments**
- Enter items by barcode scan on the New Adjustment form

---

## Architecture

### High-Level Design
Operational flow:

1. **Inventory Adjustments** page → **New Adjustment**
2. Select the storage location, enter a comment, add item lines with signed quantities
3. Submit; the system validates the location and that removals don't exceed stock
4. Success shows "Adjustment was successful." and the detail page; totals update immediately

### Components
List page (filters + table + export), New Adjustment form (line items, **Add Another Item**, barcode modal), detail page, CSV export.

### Technology Stack
Everything runs in the web dashboard — no installs or configuration for staff.

---

## Model Details

What each adjustment records:

- **Storage location** — exactly one per adjustment, owned by your organization
- **Item lines** — item + quantity; plain number adds, minus sign removes; duplicate lines for the same item merge automatically
- **Comment** — the reason (make it specific; it shows in the list and the export)
- **Creator and timestamp** — who did it, when

---

## Database Schema

Fields you'll see in the list, the detail page, and the export: created date, storage location, comment, number of changes, per-item quantities, and the creating user (available as a filter).

---

## API Endpoints

Screens and actions available to you:

| Screen | How to reach it | Purpose |
|--------|-----------------|---------|
| Inventory Adjustments | Inventory area of the dashboard | Browse/filter history |
| Adjustment detail | **View** on any row | See Added/Removed per item |
| New Inventory Adjustment | **New Adjustment** button | Record a correction |
| CSV download | **Export Adjustments** button | Spreadsheet of filtered rows |

There is no edit or delete screen — corrections of corrections are made with a new, reversing adjustment.

---

## Authorization

Sign in to your organization's bank account. You only ever see your own organization's adjustments, and you can only adjust your organization's (active) storage locations.

---

## Configuration

None required. Confirm the storage location exists and is active before adjusting it.

---

## Usage Examples

### Record a recount surplus
1. **Inventory Adjustments** → **New Adjustment**
2. Pick the storage location
3. Comment: "Oct recount — 12 extra size 3"
4. Item: Diapers size 3, quantity `12`
5. Submit → "Adjustment was successful."

### Write off damaged stock
1. **New Adjustment** → same location picker
2. Comment: "Water damage, storeroom B"
3. Item: Wipes, quantity `-40` (minus sign removes)
4. Submit

### Reverse a mistake
1. Open the wrong adjustment with **View**; note its items
2. **New Adjustment** at the same location
3. Enter each quantity with the opposite sign; comment references the original
4. Submit — totals return to their prior values; both records stay in history

---

## Testing

After saving, open the storage location and verify the new totals match your physical count before filing the paperwork.

---

## Known Issues & Caveats

| Caveat | Operational impact |
|--------|--------------------|
| Permanent records | Never try to "fix" an adjustment — reverse it with a new one |
| Removals capped at stock on hand | Oversized decreases reject the entire adjustment; nothing saves |
| One location per adjustment | Stock moves between locations are Transfers, not adjustments |
| Loose items only | Kits are not offered in the item picker |
| Export needs results | **Export Adjustments** appears only when the filtered list is non-empty |

---

## Performance

Use the filters (storage location, user, date range) on long histories; the table is paginated and the export honors the filters.

---

## Troubleshooting

### Submit fails with an inventory error
**Cause:** A removal exceeds the recorded quantity at the location.
**Solution:** Check the location's stock, lower the decrease, and resubmit. The failed attempt saved nothing.

### "Storage location must belong to organization"
**Cause:** The selected location isn't your organization's.
**Solution:** Choose one of your organization's locations.

### Error messages listed on the form
**Cause:** One or more fields are invalid; each problem is listed on its own line.
**Solution:** Fix every listed item, then submit again.

---

## Related Features

- **Transfers** — moving stock between storage locations
- **Audits** — formal physical-count verification
- **Storage Locations** — where adjusted inventory lives
- **Items** — the catalog adjusted here (loose items only)

---

**Generated:** 2026-10-24T00:00:00Z
**Last Updated:** 2026-10-24T00:00:00Z
**Status:** ✅ Active
