# Distributions

> A comprehensive guide to Distributions.

---

## What is Distributions?

Distributions are the main way supplies leave your essentials bank. Each distribution records a set of items going from one of your storage locations to one partner organization on a scheduled date, by pick up, delivery, or shipping. Saving a distribution automatically deducts the items from your inventory, and deleting ("reclaiming") one puts them back — so your on-hand counts always stay accurate.

---

## Key Capabilities

- Create a distribution from scratch, from a partner's request (the request is marked fulfilled), or starting from a donation's contents
- Preview and confirm the exact item list in a confirmation window before anything is saved
- Choose pick up, delivery, or shipped — shipped distributions can carry a shipping cost
- Automatically email the partner the details with a PDF manifest attached, notify them when a distribution changes, and send a reminder one day before the scheduled date
- View every distribution on a schedule calendar, subscribe to it from your own calendar app, and work from a pickup-day list with per-item totals
- Filter the distribution list by item, item category, reporting category, partner, status, storage location, and date range — with running totals for quantity and value
- Export spreadsheets, download an itemized breakdown of what was distributed versus what's on hand, and view estimated totals by county

---

## How It Works

1. **Create** — Choose the partner, the source storage location, the scheduled date, the delivery method, and the items with quantities. Starting from a partner request locks in the partner, pre-fills the requested items, carries over the request's comments, and sets the date to tomorrow. Items requested in a custom unit are left without a quantity on purpose — you enter the number you'll actually give.
2. **Confirm** — A confirmation window shows "You are about to create a distribution for [partner] from [location]" with the full item table. Nothing is saved until you confirm.
3. **Inventory moves** — On save, the items are deducted from the storage location. If any quantity exceeds what's on hand, the save fails and the problem items are flagged.
4. **Partner is notified** — Partners with reminders enabled get an email with the PDF manifest. If the day-before reminder is enabled, a reminder email is sent one day before the scheduled date.
5. **Complete** — Distributions move through two stages: **Scheduled** → **Complete**. When the pickup or delivery happens, one click marks it complete. Nothing moves back from complete to scheduled.
6. **Fix or undo** — Corrections adjust inventory automatically and, when the date, delivery method, or contents changed, the partner gets a "Your Distribution Has Changed" email listing what was updated or removed. Reclaiming deletes the distribution and returns all items to the storage location.

---

## Common Questions

**Q: What's the difference between correcting and reclaiming a distribution?**
A: A correction changes the details (items, quantities, date, delivery method) and keeps the record — inventory adjusts automatically. Reclaiming deletes the distribution entirely and restores every item to the storage location it came from.

**Q: Why won't my distribution save?**
A: Usually because a quantity is larger than what the storage location has on hand — the error message points out the problem items. A distribution also needs a delivery method and at least one item with a total quantity of one or more.

**Q: Can the same partner request be fulfilled twice?**
A: No. If a request already has a distribution, trying to fulfill it again is blocked with a message naming the existing distribution.

**Q: Who can edit a distribution after the fact?**
A: Anyone in the organization can edit a distribution that is still scheduled for a future date. Once it is complete or its date has passed, only an organization administrator can edit it.

**Q: What happens to the shipping cost if I change the delivery method?**
A: Shipping cost applies only to shipped distributions. If you switch to pick up or delivery, the entered shipping cost is silently discarded — re-enter it if you switch back.

**Q: Why can't I delete an old distribution?**
A: Once a newer inventory snapshot exists, distributions from before it can't be deleted or have their contents changed. The error message tells you the cutoff date.

**Q: How does the calendar subscription work?**
A: The schedule page has a button to copy a calendar link to your clipboard. Paste it into any calendar app that accepts internet calendar feeds. The link works without signing in, so anyone holding it can see your schedule — treat it as confidential.

**Q: Why didn't my partner get an email or reminder?**
A: Emails are skipped when the partner's reminder setting is off, the partner is deactivated, or the distribution's date has already passed. Reminders go out one day before the scheduled date, so same-day distributions don't get a useful reminder.

**Q: What shows up on the printed manifest?**
A: The PDF lists the items and quantities. Depending on your organization's settings it can also show item values, package counts, a year-to-date total, and signature lines — or hide the value and package columns entirely. For request-based distributions, requested quantities appear alongside what was given.

---

## Tips & Best Practices

- Review the confirmation window carefully — it's the last checkpoint before inventory is deducted.
- Enable the day-before reminder when creating distributions so partners don't miss pickups.
- Work the day from the pickup-day list: it shows each pickup's partner, time, source location, and status, plus combined item totals for staging product.
- Use the filters before exporting — the spreadsheet respects them, and the on-screen totals update to match, both for the current page and the whole filtered set.
- For pick-up distributions, extra pick-up contacts from the partner's profile are automatically copied on the notification email — keep partner profiles up to date.

---

## Limitations & Important Notes

- Each distribution has exactly one source storage location and one recipient partner — it can't be split.
- Distributions older than your latest inventory snapshot can't be deleted or have contents changed.
- Completed distributions can't be moved back to scheduled.
- The by-county report is an estimate, apportioned from each partner's declared service areas.
- The subscribable calendar link is public to anyone who has it (though protected by an unguessable code) — share it only with people who should see your pickup schedule.
- Switching the delivery method away from shipped discards the shipping cost without warning.

---

## Related Features

- **Requests** — a partner request can be fulfilled by exactly one distribution, with the partner and items pre-filled
- **Donations** — a donation's contents can seed a new distribution
- **Storage Locations** — every distribution draws down one location; only active locations with stock are offered when creating
- **Partners** — recipients; their settings control notification emails, pick-up contacts, and delivery addresses on the manifest
- **Audits** — if a location was audited after a distribution was created, the edit page warns you that physical changes also need an inventory adjustment
- **Reports** — distribution quantities and values feed summary and trend reporting
