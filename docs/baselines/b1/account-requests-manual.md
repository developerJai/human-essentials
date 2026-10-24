# Account Requests — Operations Manual

This manual is for Human Essentials operations staff (super admins) who triage incoming account requests from prospective essentials banks. It covers the request pipeline end to end: what the requester does, what emails the system sends, and the actions available to you in the admin panel.

## The pipeline at a glance

| Stage | Status shown | Who acts | What happens |
|---|---|---|---|
| 1. Submitted | Started | Requester | Public form completed (with captcha); system emails the requester a confirmation link |
| 2. Confirmed | User Confirmed | Requester | Requester clicks the confirmation link; system emails **info@humanessentials.app** with the full request details |
| 3a. Approved | Admin Approved | Ops staff | You create the organization from the request (via the "Create This Organization" link); requester receives their invitation |
| 3b. Rejected | Rejected | Ops staff | You reject with a reason; requester is emailed the reason automatically |
| 3c. Closed | Admin Closed | Ops staff | You close with a reason; **no email is sent** to the requester |

Open requests are those in **Started** or **User Confirmed**. Closed requests are **Admin Approved**, **Rejected**, or **Admin Closed**.

## What the requester submits

Name, email, organization name, organization website (optional), optional NDBN membership selection, and a free-text "Request Details" of at least 50 characters. The form enforces that the email is not already used by another request, an existing organization, or an existing user. Partner agencies are steered away from the form — only banks should apply.

## Emails sent by the system

1. **To the requester, on submission** — subject "[Action Required] Human Essential Account Request". Contains the confirmation link, demo-site credentials (data resets daily at 6 AM EST), the User Guide link, and getting-started videos. Sent from no-reply@humanessentials.app.
2. **To info@humanessentials.app, on confirmation** — subject "[Account Request] <organization name>". Lists every field of the request and contains two action links: **Create This Organization** and **Reject This Organization**.
3. **To the requester, on rejection** — subject "Human Essential Account Request Rejected", including the reason you entered, verbatim. Write rejection reasons knowing the requester reads them word for word.

No email is generated when you close a request.

## Working the queue: Admin > Account Requests

Open **Account Requests** in the admin panel. The page shows two tables:

- **Open Account Requests** — newest submissions first, 15 per page. Columns: Date Submitted, Organization Details (name and website), Request details, Request status, Contact Details (name and email), and Actions.
- **Closed Account Requests** — most recently updated first, 15 per page. Columns include Date Confirmed (or "N/A" if the requester never confirmed) and the Rejection Reason, so past decisions are auditable.

Each table paginates independently, so you can browse open and closed requests side by side.

### Rejecting a request

1. Find the row in **Open Account Requests** and click **Reject**.
2. In the modal, enter the **Rejection reason**. The reason is mandatory — the form will not submit without it ("Reason must be provided").
3. Submit. You'll be returned to the list with "Account request rejected!", and the requester is emailed the reason automatically.

You can also arrive at the rejection screen directly from the **Reject This Organization** link in the notification email; it shows just that one request with the same Reject/Close actions. If the link's token doesn't match a request, the page reports "Account Request not found!".

### Closing a request (administrative close)

Use **Close (Admin)** when a request should be shut without notifying the requester — e.g. spam, duplicates, or abandoned submissions. The flow is identical to rejection (a reason is required and is stored for the record), but **no rejection email goes out**.

Closing is only possible while the request is still open (Started or User Confirmed). Attempting to close a request that is already approved, rejected, or closed fails with "Cannot be closed from this state" shown as an alert.

### Approving a request

Approval is performed from the notification email's **Create This Organization** link, which pre-fills the new-organization form from the request. Once the organization is created, the request counts as processed: its confirmation link stops working and it moves to the closed table as Admin Approved.

## Troubleshooting

- **Requester says their confirmation link doesn't work.** Links are single-use. The page "The account request is either invalid, confirmed already, or processed already" means they already confirmed, the organization already exists, or the link was mangled. Check both tables for their request's actual status.
- **Requester never confirmed.** Their request sits in the open table as Started, with "N/A" for Date Confirmed once closed. Ask them to check spam for no-reply@humanessentials.app; if the email address was wrong they must submit a new request.
- **Close button errors with "Cannot be closed from this state".** The request was already finalized (likely by another admin, or approved via the email link). Refresh the index and verify its current status.
- **Requester wants to reuse an email from a rejected/closed request.** That is allowed — the duplicate-email restriction no longer applies once a request is rejected or closed.
