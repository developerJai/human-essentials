# Distributions — User Manual

> Step-by-step instructions for using Distributions.

---

## Prerequisites

- You must be a member of your organization; editing a distribution that is complete or whose date has passed requires an organization administrator.
- At least one active storage location with stock on hand — only active locations with stock are offered when creating a distribution.
- An active partner to receive the supplies (deactivated partners are not emailed and should be reactivated first).
- If you plan to fulfill partner requests, the request must not already have been fulfilled — each request can be fulfilled by exactly one distribution.

---

## Overview

This guide walks operations staff through the distribution workflow: creating a distribution (from scratch, from a partner request, or from a donation), confirming it, completing it on pickup day, correcting mistakes, reclaiming (undoing) a distribution, printing the manifest, and exporting data. Distributions move through two stages — **Scheduled** → **Complete** — and saving one automatically deducts the items from your inventory.

---

## Task 1: Create a Distribution

### Steps

1. Open the distributions area and start a new distribution
2. Fill in the details:
   - **Partner** — the organization receiving the supplies
   - **Scheduled date** — when the pickup, delivery, or shipment happens
   - **Delivery method** — pick up, delivery, or shipped; shipped distributions can also carry a **shipping cost**
   - **Source storage location** — where the items are deducted from
   - **Day-before reminder** — enable it to email the partner a reminder one day before the date
   - **Items and quantities** — what's going out
3. Submit the form
4. A confirmation window appears: "You are about to create a distribution for [partner] from [location]" with the full item table. Review it, then confirm

### Expected Result

The distribution is saved in **Scheduled** status and the items are deducted from the storage location. If the partner has reminders enabled, they receive an email with the PDF manifest attached. If any quantity exceeds what's on hand, the save fails and the problem items are flagged — nothing is deducted until the form passes.

---

## Task 2: Complete a Distribution

### Steps

1. On the day, work from the pickup-day list, which shows each pickup's partner, time, source location, and status, plus combined item totals for staging product
2. When the pickup or delivery happens, mark the distribution complete (one click)

### Expected Result

The distribution moves from **Scheduled** to **Complete**. Completed distributions cannot be moved back to scheduled.

---

## Task 3: Correct a Distribution

### Steps

1. Open the distribution and choose to edit it
   - Anyone can edit while it is still scheduled for a future date
   - Once it is complete or its date has passed, only an organization administrator can edit
   - If the storage location was audited after the distribution was created, a warning reminds you that physical changes also need a separate inventory adjustment
2. Change the items, quantities, date, or delivery method
3. Save

### Expected Result

Inventory adjusts automatically. If the date, delivery method, or contents changed, the partner receives a "Your Distribution Has Changed" email listing what was updated or removed (if their notifications are on).

---

## Task 4: Reclaim (Undo) a Distribution

### Steps

1. Find the distribution in the list
2. Choose reclaim and confirm

### Expected Result

The distribution is deleted entirely and every item is returned to the storage location it came from. Distributions older than your latest inventory snapshot can't be reclaimed — the error message tells you the cutoff date.

---

## Task 5: Print the Manifest

### Steps

1. Open the distribution and print the PDF manifest

### Expected Result

A PDF lists the items and quantities. Depending on your organization's settings it may also show item values, package counts, a year-to-date total, and signature lines — or hide the value and package columns. For request-based distributions, requested quantities appear alongside what was given.

---

## Variations

### Fulfilling a Partner Request

Use this when a partner has submitted a request for supplies.

1. Start the distribution from the request — the partner is locked in, requested items are pre-filled, the request's comments carry over, and the date defaults to tomorrow
2. Items requested in a custom unit have no quantity on purpose — enter the number you will actually give
3. Confirm and save; the request is marked fulfilled

A request can only be fulfilled once: trying again is blocked with a message naming the existing distribution.

### Starting from a Donation

Begin a new distribution from a donation — its contents seed the item list, ready to adjust before you confirm.

### Subscribing to the Pickup Calendar

1. Open the schedule calendar page
2. Use the button that copies the calendar link to your clipboard
3. Paste the link into any calendar app that accepts internet calendar feeds

The link works without signing in — anyone holding it can see your pickup schedule, so treat it as confidential.

---

## Settings & Configuration

Ask your administrator about these organization-level options:

| Setting | Description | Default |
|---------|-------------|---------|
| Manifest value columns | Show or hide item values on the PDF | Shown |
| Manifest package column | Show or hide package counts on the PDF | Shown |
| Year-to-date on manifest | Add a year-to-date items total to the PDF | Off |
| Signature lines | Add signature lines to the PDF | Off |
| Partner reminder setting | Per partner: whether they receive distribution emails and reminders | Partner-specific |
| Partner pick-up contacts | Extra contacts copied on pick-up notification emails | From partner profile |

---

## Troubleshooting

### The distribution won't save

**Cause:** a quantity is larger than what the storage location has on hand, the delivery method is missing, or no item has a quantity of one or more.
**Solution:** check the flagged items, lower quantities or switch to a location with stock, and resubmit.

### I can't edit a past or completed distribution

**Cause:** once a distribution is complete or its date has passed, editing requires an organization administrator.
**Solution:** ask an administrator to make the correction.

### I can't delete an old distribution

**Cause:** a newer inventory snapshot exists; distributions from before it can't be deleted or have contents changed.
**Solution:** none — this protection is intentional. The error message tells you the cutoff date.

### The partner never received an email or reminder

**Cause:** the partner's reminder setting is off, the partner is deactivated, or the distribution's date has already passed. Reminders go out one day before, so same-day distributions get no useful reminder.
**Solution:** check the partner's settings and the scheduled date; reactivate the partner if needed.

### The shipping cost disappeared

**Cause:** shipping cost applies only to shipped distributions — switching the delivery method to pick up or delivery silently discards it.
**Solution:** switch back to shipped and re-enter the cost.
