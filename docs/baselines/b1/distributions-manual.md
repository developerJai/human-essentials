# Distributions — User Manual (Operations Staff)

This manual walks operations staff through the day-to-day work of creating, managing, completing, and correcting distributions.

## Before you start

- You must belong to the organization and be signed in. Editing past or completed distributions requires the organization admin role.
- The storage location you distribute from must be active and have inventory on hand.
- The partner must not be deactivated (deactivated partners don't appear when creating a distribution).

## Creating a distribution

1. Go to **Distributions** and click **New Distribution**.
2. Fill in the form:
   - **Partner** — who the items are going to.
   - **Distribution date and time** — when it will be picked up, delivered, or shipped (time picker moves in 15-minute steps).
   - **Send email reminder the day before?** — tick to send the partner an automatic reminder one day before the date.
   - **Agency representative** — optional contact name/email for the partner agency.
   - **Delivery method** — Pick up, Delivery, or Shipped. Choosing **Shipped** reveals a **Shipping cost** box; for the other methods any shipping cost is discarded.
   - **Source storage location** — where the items come from.
   - **Comment** — optional notes; these also appear on the PDF and in partner emails.
   - **Items in this distribution** — pick each item and quantity. Use **Add Another Item** for more rows. Duplicate rows for the same item are combined automatically.
3. Click the submit button. A **Distribution Confirmation** window lists the partner, source location, and every item with its quantity.
4. Check the list, then click **Yes, it's correct** (or **No, I need to make changes** to go back).

**Expected result:** You land on the distribution page with "Distribution created!". The new row is highlighted on the Distributions list. Inventory at the source location is reduced immediately. If the partner has notifications on, they receive an email with a PDF of the distribution. If any item falls below your minimum or recommended level, a warning banner tells you.

**If it fails:** The form reappears with "Sorry, we weren't able to save the distribution." plus details — usually an item quantity larger than what's on hand. Fix the quantities and resubmit.

### Creating from a partner request

Open the request and start a distribution from it. The partner is locked, the requested items and quantities are pre-filled (items requested in custom units leave the quantity blank for you to decide), the request's comments carry over, and the date defaults to tomorrow. Once saved, the request is marked fulfilled — a request can only be fulfilled once.

### Creating from a donation

When starting a new distribution from a donation, the donation's items and quantities are pre-filled; adjust as needed.

## Daily operations

### See today's pickups

1. Go to **Distributions > Schedule** to view the calendar. Completed and scheduled distributions are color-coded.
2. Click a day (or go to the **Pickup Day** view) to see that day's list: partner, time, source inventory, total items, and status.
3. Below the list, **Item totals** aggregates every item going out that day with quantities and package counts — use it to stage product.

### Subscribe to the calendar

On the Schedule page, click **Copy Calendar URL to clipboard** and paste the link into Google Calendar (or any app that accepts ICS feeds). Each pickup shows as a 15-minute event named "Pickup from <partner>" at the storage location's address.

### Mark a distribution complete

When a partner picks up (or the delivery is made):

1. Open the distribution (or find it on the pickup-day list).
2. Click **Distribution Complete**.

**Expected result:** "This distribution has been marked as being completed!" and the status changes from **Scheduled** to **Complete**.

### Print the packing slip

Click the **Print** button on the distribution row or detail page. A PDF opens inline, named "<Partner> <date>.pdf", showing your logo, the partner contact, items, values, and (depending on your organization's settings) signature lines, year-to-date totals, and package columns. For requests, the PDF compares Requested vs Received quantities.

## Correcting a distribution

1. Open the distribution and click **Make a Correction** (also available as **Edit** on the list).
   - Available to everyone while the distribution is scheduled for a future date; for past or completed distributions only organization admins can edit.
   - Disabled when the distribution contains inactive items — reactivate those items first.
2. Heed any warnings:
   - *Past date warning* — the record should match what was actually handed out.
   - *Audit warning* — if you audited the location since this distribution started and the physical amounts changed, also make an inventory adjustment.
3. Change items, quantities, dates, or delivery method and submit. Setting an item's quantity to zero removes it.

**Expected result:** "Distribution updated!" Inventory is adjusted automatically. If the date, delivery method, or item contents changed and the partner has notifications on, they receive a "Your Distribution Has Changed" email listing updated and removed items.

## Reclaiming (undoing) a distribution

1. On the Distributions list, click **Reclaim** on the row.
2. Confirm the prompt ("Are you sure you want to reclaim this distribution to <partner>?").

**Expected result:** "Distribution <id> has been reclaimed!" The distribution is deleted and all items return to the source storage location. Note: distributions created before the latest inventory snapshot cannot be reclaimed; the error names the cutoff date.

## Filtering and exporting

- On the Distributions list, filter by **Item**, **Item Category**, **Reporting Category**, **Partner**, **Source Inventory**, **Status**, and **Date Range**. Totals at the bottom show items and value for the page and overall; when filtered by item/category, the totals count only the filtered items.
- **Export Distributions** downloads a CSV of the filtered list with one column per item (plus optional in-kind value and package columns, per organization settings).
- The **itemized breakdown** export produces a CSV of each item's total distributed vs. current on-hand quantity for the selected date range.
- **Distributions by County** shows estimated items and market value per county, apportioned by each partner's service-area percentages.

## Troubleshooting

| Problem | Cause | Fix |
|---|---|---|
| "Sorry, we weren't able to save the distribution." | An item's quantity exceeds on-hand inventory, or no item has quantity ≥ 1. | Reduce quantities, choose another location, or add inventory, then resubmit. |
| Can't edit — redirected with an error | You're not an org admin and the distribution is past or complete. | Ask an organization admin to make the correction. |
| **Edit**/**Reclaim** disabled, "Has Inactive Items" | An item in the distribution was deactivated. | Reactivate the item(s), then edit. |
| Partner didn't get the email | The partner has reminders/notifications turned off, is deactivated, or the distribution date is already past. | Check the partner's notification settings and the distribution date. |
| Reminder email never arrived | Reminder checkbox was off, or the distribution was created/edited less than a day before (or after) the date. | Reminders send one day before the scheduled date only for future distributions. |
| Storage location missing from the dropdown | The location is inactive or has no positive inventory. | Activate it or transfer stock in. |
