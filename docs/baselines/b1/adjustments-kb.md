# Understanding Inventory Adjustments

Sometimes the quantity your bank's system shows for an item doesn't match what is actually on the shelf. Items get miscounted, damaged, or recorded against the wrong location. **Inventory Adjustments** are how you fix that: an adjustment lets you manually increase or decrease the amount of inventory recorded at a particular storage location, with a comment explaining why.

## What an adjustment is

An adjustment is a dated record that says, in effect, "at this storage location, add this many of these items and/or remove this many of those items." Each adjustment:

- applies to **one storage location** within your organization,
- can contain **multiple items**, each with its own increase or decrease,
- records **who made it** and **when**,
- carries a **comment** so your team knows the reason later.

Positive quantities add inventory; negative quantities remove it. One adjustment can mix both — for example, +10 size 4 diapers and −3 size 5 diapers in the same record.

## Where to find it

Adjustments live in the Inventory area of your bank's dashboard. The **Inventory Adjustments** page lists every adjustment your organization has made, newest first, showing when it was created, the storage location, the comment, and a summary of how many item changes it contained. Click **View** on any row to see the full detail — each item marked as "Added" or "Removed" with its quantity.

You can narrow the list by:

- **Storage location** — only locations that actually have adjustments appear in the filter,
- **User** — who created the adjustment,
- **Date range** — using the date picker.

## Creating an adjustment

From the list page, choose **New Adjustment**. Pick the storage location, write a comment (a short reason such as "Annual recount — found 12 extra"), and add items one at a time. Enter a plain number to add that many of an item, or a negative number (with a minus sign) to subtract. You can keep clicking **Add Another Item** for as many items as you need, and barcode scanning is supported to speed up item entry.

When you submit, the system checks everything and either saves the adjustment ("Adjustment was successful.") or shows you exactly what needs fixing.

## Good to know

- **Adjustments can't be edited or deleted.** Once saved, an adjustment is permanent. If you made a mistake, create a new adjustment that reverses it (for example, if you added 10 too many, create another adjustment removing 10). This keeps a trustworthy audit trail.
- **You can't remove more than you have.** If a decrease would take an item below zero at that location, the adjustment is rejected with an error and nothing is saved.
- **Only your own locations work.** The storage location must belong to your organization.
- **Kits aren't adjustable here.** The item list only offers individual (loose) items, not kits.
- **Duplicates are merged.** If you list the same item twice, the quantities are combined into one line automatically.
- **Everything is attributed.** Each adjustment stores the user who created it, and the list can be filtered by that user.

## Exporting your adjustments

When your filtered list has at least one adjustment, an **Export Adjustments** button appears. It downloads a spreadsheet (CSV) of the adjustments currently matching your filters. Each row shows the date, storage area, comment, and the number of item updates, followed by a column for every item your organization carries with the net quantity change for that adjustment. The file is named with the current date, e.g. `Adjustments-2026-10-24.csv`.

## Frequently asked questions

**Why would I use an adjustment instead of a donation or distribution?**
Donations, purchases, and distributions record real inventory movements in and out of your bank. Adjustments are for *corrections* — bringing the system in line with reality after a recount, damage, loss, or data-entry mistake.

**Can I adjust two storage locations at once?**
No. Each adjustment applies to exactly one storage location. Moving stock between locations is what Transfers are for.

**What happens to my inventory totals?**
They update immediately: the location's item quantities go up or down by the amounts you entered, and the change flows through to reports and the dashboard.

**Who can see adjustments?**
Anyone in your organization with access to the inventory pages can view the adjustments list and details for your organization. Other organizations never see them.
