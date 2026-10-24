# Distributions — User Manual

> Step-by-step instructions for using Distributions.

---

## Prerequisites

- You must be signed in as a member of your organization. Editing past or completed distributions additionally requires the organization admin role.
- At least one active storage location with inventory on hand (locations without stock don't appear when creating).
- At least one active partner (deactivated partners can't receive distributions).
- Items set up in your inventory; items later deactivated will block editing of distributions containing them.

---

## Overview

This guide walks operations staff through the full distribution workflow: creating a distribution (including from a partner request or a donation), confirming it, running a pickup day, marking distributions complete, printing manifests, correcting mistakes, reclaiming distributions, and exporting data.

---

## Task 1: Create a Distribution

### Steps

1. Navigate to **Distributions** and click **New Distribution** (top right of the filter card)
2. Fill in the form:
   - **Partner** — the organization receiving the supplies (required)
   - **Distribution date and time** — when it goes out; the time picker moves in 15-minute steps
   - **Send email reminder the day before?** — tick to email the partner one day before the date
   - **Agency representative** — optional contact for the partner agency
   - **Delivery method** — choose **Pick up**, **Delivery**, or **Shipped**; choosing **Shipped** reveals a **Shipping cost** field
   - Source storage location — where the items are deducted from
   - **Comment** — optional; appears on the PDF and in the partner email
   - **Items in this distribution** — pick each item and quantity; click **Add Another Item** for more rows (duplicate rows for the same item are combined automatically)
3. Click the submit button
4. In the **Distribution Confirmation** window, check the partner, source location, and item list, then click **Yes, it's correct** (or **No, I need to make changes** to go back)

### Expected Result

You're taken to the distribution page with the message "Distribution created!". The new distribution is highlighted on the Distributions list, inventory at the source location is reduced, and — if the partner has notifications on — they receive an email with the PDF attached. If stock fell below your minimum or recommended levels, a warning banner appears.

If the save fails, the form reappears with "Sorry, we weren't able to save the distribution." and details — usually a quantity above what's on hand. Fix the flagged items and resubmit.

---

## Task 2: Mark a Distribution Complete

### Steps

1. Open the distribution (or find it on the Pickup Day list)
2. Click **Distribution Complete**

### Expected Result

"This distribution has been marked as being completed!" — the status changes from **Scheduled** to **Complete**.

---

## Task 3: Correct a Distribution

### Steps

1. Open the distribution and click **Make a Correction** (on the list this is the edit action)
2. Read any warning banners:
   - a caution when the scheduled date has passed (the record should match what was actually given out)
   - an audit caution if the location was audited after this distribution was started — physical changes also need an inventory adjustment
3. Change the items, quantities, date, or delivery method; setting a quantity to zero removes that line
4. Submit and re-confirm

### Expected Result

"Distribution updated!" Inventory adjusts automatically. If the date, delivery method, or contents changed and the partner has notifications on, they receive a "Your Distribution Has Changed" email listing updated and removed items.

---

## Task 4: Reclaim (Undo) a Distribution

### Steps

1. On the **Distributions** list, find the row and click **Reclaim**
2. Confirm the prompt "Are you sure you want to reclaim this distribution to [partner]?"

### Expected Result

"Distribution [id] has been reclaimed!" The record is deleted and all items return to the source storage location. Note: distributions older than your latest inventory snapshot can't be reclaimed — the error names the cutoff date.

---

## Task 5: Run a Pickup Day

### Steps

1. Navigate to **Distributions > Schedule** to open the calendar (completed and scheduled pickups are color-coded)
2. Click a day's entry to open the **Distribution Schedule** for that date
3. Stage product using the **Item totals** table (item, quantity, number of packages)
4. As each partner collects, click **Distribution Complete** on their row

### Expected Result

Each completed row's status flips to Complete; the item totals tell you exactly what to have ready for the whole day.

---

## Task 6: Print the Manifest (PDF)

### Steps

1. Click **Print** on a distribution row or on the distribution page

### Expected Result

A PDF opens in the browser named "[Partner] [date].pdf" showing your logo, organization and partner contact details, the item list with values, and — depending on your organization's settings — year-to-date totals, package counts, and "Received By:"/"Delivered By:" signature lines. For request-based distributions the table compares Requested vs Received quantities.

---

## Variations

### Creating from a Partner Request

Use this when fulfilling a request a partner submitted.

1. Start the distribution from the request
2. The **Partner** is locked, requested items and quantities are pre-filled, the request's comments carry over, and the date defaults to tomorrow
3. Items requested in custom units leave the quantity blank — enter the number you'll actually give
4. Confirm and save; the request is marked fulfilled (a request can only be fulfilled once)

### Creating from a Donation

Start a new distribution from a donation: its items and quantities arrive pre-filled, ready to adjust before confirming.

### Subscribing to the Pickup Calendar

1. On **Distributions > Schedule**, click **Copy Calendar URL to clipboard**
2. Paste the link into Google Calendar (or any app accepting ICS feeds)

Each pickup appears as a 15-minute event called "Pickup from [partner]" at the storage location's address. The link works without signing in — treat it as confidential.

---

## Settings & Configuration

These organization-wide settings (managed by your administrator) change what distributions produce:

| Setting | Description | Default |
|---------|-------------|---------|
| Hide value columns on receipt | Removes value columns from the PDF | Off |
| Hide package column on receipt | Removes the Packages column from the PDF | Off |
| Year-to-date on printout | Adds "Items Received Year-to-Date" to the PDF | Off |
| Signature lines on PDF | Adds Received By / Delivered By signature lines | Off |
| In-kind values in exports | Adds per-item In-Kind Value columns to the CSV | Off |
| Packages in exports | Adds per-item Packages columns to the CSV | Off |
| Default email text | The standard message in partner notification emails | Empty |

Per-partner: the partner's reminder/notification preference controls whether they receive any distribution emails.

---

## Troubleshooting

### Edit or Reclaim is greyed out with "Has Inactive Items"

**Cause:** the distribution contains items that were deactivated after it was created.
**Solution:** reactivate those items, make your change, then deactivate them again if needed.

### "Sorry, we weren't able to save the distribution."

**Cause:** a quantity exceeds the on-hand amount at the chosen storage location, or no line has a quantity of 1 or more.
**Solution:** lower the flagged quantities, pick a different storage location, or add stock, then resubmit.

### Redirected with "To edit a distribution, you must be an organization admin or the current date must be later than today."

**Cause:** the distribution is complete or its date has passed, and you don't have the admin role.
**Solution:** ask an organization administrator to make the correction.

### The partner never received the email or reminder

**Cause:** the partner's notifications are off, the partner is deactivated, or the distribution's date had already passed; reminders are only sent one day before future distributions.
**Solution:** check the partner's settings and the scheduled date.

### A storage location is missing from the dropdown

**Cause:** the location is inactive or has no positive inventory.
**Solution:** reactivate the location or transfer stock into it, then reload the form.
