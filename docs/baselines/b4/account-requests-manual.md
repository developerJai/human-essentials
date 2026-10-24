# Account Requests — User Manual

> Step-by-step instructions for using Account Requests.

---

## Prerequisites

- No account or login is needed to apply — the request form is public, but you must complete a captcha
- You must be an **essentials bank**; partner agencies do not apply here (their accounts are created by their banks)
- Use an email address that is not already attached to any Human Essentials organization, user, or request
- Apply on the live Human Essentials website — the form on the demo/staging site is disabled and only points you to the production form

---

## Overview

This guide walks a new essentials bank through requesting a Human Essentials account: submitting the application form, confirming the request by email, and understanding the review outcomes (approval, rejection, or administrative closure). The review itself is performed by the Human Essentials team, who are notified once you confirm.

---

## Task 1: Submit an Account Request

### Steps

1. Open the **Essentials Bank Account Request Form** on the live Human Essentials website
2. Select **I am an Essentials Bank** (choosing **I am a Partner Agency** routes you away from the form instead, since partner accounts are created by your bank)
3. Fill in the fields:
   - **Name** — your name
   - **Email** — must not already be used by another request, an existing organization, or an existing user
   - **Organization name** — your bank's name
   - **Organization website** — optional; if provided, it must be a full address like `https://www.example.com`
   - **NDBN membership** — optional; select yours from the list
   - **Request details** — at least 50 characters describing your organization; the review team reads exactly what you type
4. Complete the **captcha**
5. Submit the form

### Expected Result

You see the **"Request Received!"** page. A confirmation email is sent to your address from **no-reply@humanessentials.app** — check your spam filters if it doesn't arrive. Your request is now in the **Started** stage.

---

## Task 2: Confirm Your Request

### Steps

1. Open the confirmation email from **no-reply@humanessentials.app**
2. Click the confirmation link (copy the entire link if clicking doesn't work — truncated links are a common cause of errors)
3. On the page asking **"Are you ready to get started?"**, click **I'm ready! Let's go!**

### Expected Result

You see **"Confirmed! We will be processing your request now."** The Human Essentials team at info@humanessentials.app is notified of your confirmed request. The confirmation link stops working from this point — it is effectively single-use.

---

## Task 3: Receive the Review Outcome

### Steps

1. Wait for the team's review — they are only notified after you confirm, so confirm promptly
2. Watch your inbox (and spam folder) for the outcome

### Expected Result

One of three outcomes:

- **Approved** — your organization is created, and your bank's administrator receives an invitation email to set up access
- **Rejected** — you receive an email containing the team's reason, word for word
- **Closed** — the team closed the request administratively; a reason is recorded internally but **no email is sent to you**

> Requests move through stages: **Started** → **Confirmed by you** → **Approved**, **Rejected**, or **Closed by the team**

---

## Variations

### You are a partner agency, not a bank

Partner agencies never apply through this form. Select **I am a Partner Agency** on the form and you'll be routed accordingly — your account must be created by the essentials bank you partner with.

### Applying again after a rejection or closure

Once a request is rejected or closed, its email address is freed up:

1. Return to the **Essentials Bank Account Request Form**
2. Submit a new request — you may reuse the same email address
3. Confirm from the new email as in Task 2

### Exploring the sandbox first

A sandbox site exists for trying the app out. Note that its data resets every day at **6 AM EST**, and account requests cannot be submitted from the staging site itself.

---

## Settings & Configuration

There are no user-configurable settings for this feature. Fixed behaviors to know:

| Setting | Description | Default |
|---------|-------------|---------|
| Request details length | Minimum characters required | 50 |
| Website format | Must look like a full URL | `https://www.example.com` style (optional field) |
| Confirmation link | Reusable? | No — stops working once confirmed or processed |
| Closure notification | Email sent when the team closes a request | None |
| Sender address | Where system emails come from | no-reply@humanessentials.app |
| Audit history | Changes to your request are recorded | Always on |

---

## Troubleshooting

### The confirmation link shows "The account request is either invalid, confirmed already, or processed already."

**Cause:** Confirmation links are single-use — you already confirmed, your organization has already been created, or the link was truncated when copied.
**Solution:** If your request is genuinely still pending, copy the complete link from the email and try again. If you already confirmed, simply wait for the outcome email.

### The form rejects your email address

**Cause:** The address is already used by another account request, an existing organization, or an existing user.
**Solution:** Use a different email address, or sign in with your existing account instead of applying.

### No confirmation email arrives

**Cause:** Spam filtering of mail from no-reply@humanessentials.app.
**Solution:** Check your spam folder. Both the confirmation and later correspondence come from that address.

### You were rejected or never heard back

**Cause:** Rejections always include the team's reason by email. Closures, however, send no notification at all.
**Solution:** Read the reason in the rejection email, address it, and apply again — your email address is freed up once a request is rejected or closed.

### Nothing happens after submitting on the demo/staging site

**Cause:** The request form on the staging site is disabled; it only points to the production form.
**Solution:** Submit your application on the live Human Essentials website.
