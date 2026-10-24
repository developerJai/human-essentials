# Account Requests — User Manual

> Step-by-step instructions for using Account Requests.

---

## Prerequisites

- To triage requests you need **super admin** access to the Human Essentials admin panel
- Applicants need no account or permission — the request form is public, but a captcha must be completed
- The ops mailbox **info@humanessentials.app** should be monitored: approval/rejection action links arrive there

---

## Overview

This guide covers the full account-request workflow: how a prospective essentials bank submits and confirms a request, and how operations staff review, reject, or close requests from **Admin > Account Requests**. Approval itself is finished on the new-organization form reached from the notification email.

---

## Task 1: Submit an Account Request (applicant)

### Steps

1. Go to the public **Essentials Bank Account Request Form**
2. Select **I am an Essentials Bank** (partner agencies must not apply — their bank creates their account; the partner option shows sign-in and directory links instead of a form)
3. Fill in the required fields:
   - **Name** — your name
   - **Email** — must not already be used by an existing organization, user, or request
   - **Organization name** — your bank's name
   - **Organization website** — optional; must look like `https://www.example.com`
   - **NDBN Membership** — optional; pick your organization from the list
   - **Request Details (min 50 characters)** — tell the team more about your organization and how you would use Human Essentials
4. Complete the captcha
5. Click **Submit**

### Expected Result

You see the **"Request Received!"** page confirming an email was sent to your address, with a reminder to check spam for **no-reply@humanessentials.app**. The page URL confirms the notice "Account request was successfully created."

---

## Task 2: Confirm the Request (applicant)

### Steps

1. Open the email **"[Action Required] Human Essential Account Request"**
2. Click **Confirm This Request**
3. On the "Are you ready to get started?" page, click **I'm ready! Let's go!**

### Expected Result

A page reading **"Confirmed! We will be processing your request now."** The team is notified immediately and will email your invitation once processed. If the link was already used or the account already exists, you instead see: "The account request is either invalid, confirmed already, or processed already."

---

## Task 3: Review the Queue (operations staff)

### Steps

1. Navigate to **Admin > Account Requests**
2. Review the **Open Account Requests** table (newest first, 15 per page): **Date Submitted**, **Organization Details**, **Request details**, **Request status** (Started or User Confirmed), **Contact Details**, **Actions**
3. Scroll down to **Closed Account Requests** (most recently updated first, 15 per page) for history, including **Date Confirmed** ("N/A" if never confirmed) and **Rejection Reason**

### Expected Result

A complete picture of pending and decided requests; the two tables page independently.

---

## Task 4: Reject a Request (operations staff)

### Steps

1. In **Open Account Requests**, click **Reject** on the request's row
2. In the modal, enter the **Rejection reason** — it is required; leaving it blank shows "Reason must be provided"
3. Click the submit button

### Expected Result

You return to the list with the message **"Account request rejected!"**. The applicant automatically receives an email, "Human Essential Account Request Rejected", containing your reason word for word.

---

## Task 5: Close a Request Administratively (operations staff)

### Steps

1. In **Open Account Requests**, click **Close (Admin)** on the row
2. Enter a reason in the modal (required; stored for the record)
3. Submit

### Expected Result

**"Account request closed!"** — the request moves to the closed table with your reason under Rejection Reason. **No email is sent** to the applicant. If the request was already finalized, an alert shows "Cannot be closed from this state".

---

## Variations

### Rejecting straight from the notification email

When an applicant confirms, info@humanessentials.app receives "[Account Request] <organization name>" listing every detail of the request.

1. Click **Reject This Organization** in that email
2. The single request opens with the same row layout and **Reject** / **Close (Admin)** buttons
3. Proceed as in Task 4 or 5

If the link no longer matches a request, the page shows "Account Request not found!".

### Approving a request

1. In the same notification email, click **Create This Organization**
2. Complete the new-organization form it opens (pre-linked to the request)
3. The request becomes **Admin Approved**, appears in the closed table, and the applicant's confirmation link stops working

---

## Settings & Configuration

There are no user-facing settings for this feature. Fixed behaviors worth knowing:

| Setting | Description | Default |
|---------|-------------|---------|
| Page size | Rows per table in the admin queue | 15 |
| Open sort order | By submission date | Newest first |
| Closed sort order | By last update | Newest first |
| Ops notification address | Where confirmed requests are announced | info@humanessentials.app |
| Sender address | All applicant emails | no-reply@humanessentials.app |

---

## Troubleshooting

### The applicant's confirmation link shows "invalid, confirmed already, or processed already"

**Cause:** The link is single-use. The request was already confirmed, the organization already created, or the URL was truncated.
**Solution:** Look the request up in both admin tables. If it is **User Confirmed**, simply process it; if still **Started**, ask the applicant to copy the full link from the email.

### "Cannot be closed from this state" when closing

**Cause:** Only requests in **Started** or **User Confirmed** can be closed; this one was already approved, rejected, or closed — possibly by another admin or via the email links.
**Solution:** Refresh **Admin > Account Requests** and check the closed table for its final status.

### The rejection modal won't submit

**Cause:** The **Rejection reason** field is empty — the form blocks submission and shows "Reason must be provided".
**Solution:** Enter a reason. Remember the applicant reads it verbatim in the rejection email (for closes, it is stored but never emailed).

### Applicant reports no confirmation email

**Cause:** Spam filtering, or a mistyped address at submission.
**Solution:** Have them search spam for **no-reply@humanessentials.app**. If the address was wrong, they must submit a new request; the old one can be closed with **Close (Admin)**.

### Form keeps saying "Invalid captcha submission"

**Cause:** The captcha wasn't completed (or failed verification).
**Solution:** The applicant must complete the captcha widget and resubmit.
