# Distributions

> A comprehensive guide to Distributions.

---

## What is Distributions?

Distributions are how supplies leave your essentials bank and reach the families you serve. Each distribution records a set of items going from one of your storage locations to one partner organization on a scheduled date. It keeps your inventory accurate automatically, sends your partner the paperwork, and feeds your reports.

---

## Key Capabilities

- Create a distribution from a blank form, from a partner's request, or starting from a donation's contents
- Review and confirm the exact item list before anything is saved
- Choose how the supplies get to the partner: pick up, delivery, or shipped (with a shipping cost)
- Email the partner automatically with a PDF summary, and optionally remind them the day before
- See every scheduled pickup on a calendar and subscribe to it from your own calendar app
- Work from a daily pickup list with combined item totals
- Mark distributions complete, correct mistakes, or undo ("reclaim") a distribution entirely
- Export to spreadsheets and view estimated totals by county

---

## How It Works

1. **Create** — Choose the partner, the storage location the supplies come from, the date and time, the delivery method, and the items with quantities. Starting from a partner request pre-fills the partner and the requested items, and the date defaults to tomorrow.
2. **Confirm** — Before saving, a confirmation window lists the partner, the source location, and every item with its quantity. Nothing happens to your inventory until you confirm.
3. **Inventory moves** — On confirmation, the items are deducted from the chosen storage location. If any item would go below what's on hand, the save is rejected and the problem items are pointed out. You're also warned when stock drops below your minimum or recommended levels.
4. **Partner is notified** — Partners with notifications enabled receive an email with the details and a PDF attachment. If you ticked the reminder option, a reminder email goes out one day before the scheduled date.
5. **Hand over and complete** — On the day, the pickup happens (or the delivery/shipment goes out) and you mark the distribution complete.

Distributions move through two stages: **Scheduled** → **Complete**.

If something was recorded wrong, you can correct the distribution (inventory adjusts automatically and the partner can be notified of the changes) or reclaim it, which deletes the record and returns every item to the storage location.

---

## Common Questions

**Q: What's the difference between correcting and reclaiming a distribution?**
A: Correcting changes the details — items, quantities, date, or delivery method — and keeps the record. Reclaiming deletes the distribution entirely and puts all of its items back into the storage location it came from.

**Q: Why won't my distribution save?**
A: Almost always because a quantity is larger than what the storage location has on hand — the message tells you which items are short. A distribution also needs a delivery method and at least one item with a quantity of one or more.

**Q: Can I fulfill the same partner request twice?**
A: No. Once a request has been fulfilled by a distribution, trying to create another from it is blocked, and you're pointed to the existing distribution.

**Q: Who receives the distribution emails?**
A: When the distribution came from a partner request, the person who made the request receives it, with the partner's main email copied. For pick-up distributions, any additional pick-up contacts from the partner's profile are copied too. Partners with notifications turned off receive nothing.

**Q: Can I edit a distribution after its date has passed?**
A: Only organization administrators can edit past or completed distributions. Everyone else can edit a distribution only while it's scheduled for a future date.

**Q: Why is the Edit (or Reclaim) option unavailable on some distributions?**
A: The distribution contains items that have since been deactivated. Reactivate those items first, and the options come back.

**Q: What happens to the shipping cost if I change the delivery method?**
A: The shipping cost only applies to shipped distributions. If you switch to pick up or delivery, the cost is cleared automatically.

**Q: How does the calendar subscription work?**
A: From the schedule page you copy a private calendar link and add it to Google Calendar or any calendar app. It shows your pickups from the last year onward, each with the partner's name and the storage location's address. The link works without logging in, so share it carefully.

**Q: Why did I see a warning about an audit when editing?**
A: Your team audited that storage location after the distribution was created. If you're fixing a typo, carry on; if the physical amounts actually changed, you'll also need a separate inventory adjustment.

**Q: Why can't I delete a very old distribution?**
A: Once a newer inventory snapshot exists, distributions from before it can't be deleted. The error message tells you the cutoff date.

---

## Tips & Best Practices

- Read the confirmation window carefully — it's your last checkpoint before inventory is deducted.
- Turn on the day-before reminder when you create the distribution so partners don't miss pickups.
- Start the morning from the pickup-day view: it lists every pickup for the day plus combined item totals, perfect for staging product.
- When fulfilling requests that use custom units (like packs), the quantity is left blank on purpose — decide and enter the number yourself.
- Use the filters (item, category, partner, status, location, date range) before exporting so your spreadsheet contains exactly what you need; the totals at the bottom update to match the filter.

---

## Limitations & Important Notes

- A distribution draws from exactly one storage location and goes to exactly one partner — it can't be split.
- Distributions older than your latest inventory snapshot can't be deleted or have their contents changed.
- No emails are sent for distributions whose date is already in the past, and reminders can't go out for same-day distributions (they're sent one day before).
- The by-county report is an estimate: totals are apportioned using each partner's declared service-area percentages, with anything unmatched shown as "Unspecified".
- Switching delivery method away from "Shipped" silently discards the shipping cost you entered.

---

## Related Features

- **Requests** — partners ask for supplies; fulfilling a request creates its distribution with everything pre-filled
- **Donations** — a donation's contents can seed a new distribution
- **Storage Locations** — the source of every distribution; low-stock warnings appear when a distribution dips below your minimums
- **Partners** — the recipients; their profile controls email notifications, pick-up contacts, and delivery addresses
- **Reports** — distribution quantities and values flow into summary and county reports
