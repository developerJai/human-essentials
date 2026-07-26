# Partners (Bank-Side Management) User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.

## Overview

The Partners page is where your essentials bank manages partner agencies. You can create new partners, invite them to the partner portal, review and approve their applications, manage their status (approve, deactivate, reactivate, request recertification), and import partners in bulk via CSV. Partners go through a lifecycle: uninvited, invited, awaiting review, approved, and optionally deactivated or pending recertification.

---

## Task 1: View All Partners

### Steps

1. In the left sidebar, click **Partner Agencies** to expand the menu.
2. Click **All Partners**.
3. On the **Partner Agencies** page, the **Partners** tab is active by default.
4. The table shows all partners with their names, status, and available actions.

### Expected Result

You see a list of all partner agencies for your organization with their current status.

---

## Task 2: Create a New Partner

### Steps

1. Navigate to the **Partner Agencies** page.
2. Click the **New Partner** button.
3. In the **Name** field, enter the partner agency's name.
4. In the **Email** field, enter the primary contact email for the partner.
5. (Optional) Fill in additional fields such as address, notes, or partner group assignment.
6. Click the **Save** button.

### Expected Result

The partner is created with an "uninvited" status. They have not yet been invited to log in to the partner portal.

---

## Task 3: Invite a Partner

### Steps

1. On the **Partner Agencies** page, find the uninvited partner.
2. Click the **Invite** button in the actions column for that partner.
3. Confirm the invitation when prompted.

### Expected Result

An invitation email is sent to the partner's email address with instructions to set up their account and log in to the partner portal. The partner's status changes to "invited."

---

## Task 4: Approve a Partner

### Steps

1. On the **Partner Agencies** page, find a partner with "awaiting review" status.
2. Click the **Approve** button in the actions column.
3. Confirm the approval when prompted.

### Expected Result

The partner's status changes to "approved." They can now submit requests through the partner portal.

---

## Task 5: View Partner Details

### Steps

1. On the **Partner Agencies** page, find the partner you want to review.
2. Click the **View** button (or the partner's name) in the actions column.

### Expected Result

The partner detail page shows the partner's profile information, contact details, status, associated distributions, and request history.

---

## Task 6: Edit a Partner

### Steps

1. On the **Partner Agencies** page, find the partner you want to edit.
2. Click the **Edit** button.
3. Update the partner's **Name**, **Email**, **Notes**, **Partner Group**, or other fields.
4. Click the **Save** button.

### Expected Result

The partner's information is updated.

---

## Task 7: Deactivate a Partner

### Steps

1. On the **Partner Agencies** page, find the approved partner you want to deactivate.
2. Click the **Deactivate** button in the actions column.
3. Confirm the deactivation when prompted.

### Expected Result

The partner's status changes to "deactivated." They can no longer submit requests through the partner portal. Their historical data is preserved.

---

## Task 8: Reactivate a Partner

### Steps

1. On the **Partner Agencies** page, find the deactivated partner.
2. Click the **Reactivate** button in the actions column.
3. Confirm the reactivation when prompted.

### Expected Result

The partner's status returns to "approved" and they can once again submit requests through the partner portal.

---

## Task 9: Request Recertification from a Partner

### Steps

1. On the **Partner Agencies** page, find the partner that needs recertification.
2. Click the **Recertify** button in the actions column.
3. Confirm the action when prompted.

### Expected Result

The partner's status changes to indicate recertification is pending. The partner receives a notification to update their profile information through the partner portal. Once they submit updated information, their status returns to "awaiting review" for your approval.

---

## Task 10: Import Partners from CSV

### Steps

1. Navigate to the **Partner Agencies** page.
2. Click the **Import Partners** button to open the CSV import modal.
3. Download the CSV template by clicking the template link.
4. Open the template in a spreadsheet program, delete the sample data, and enter your partner agency names and addresses in the appropriate columns.
5. Save the file as a CSV file.
6. Back in the import modal, click **Choose File** and select your CSV file.
7. Click **Upload** to import the partners.

### Expected Result

Partners from your CSV file are created in the system with "uninvited" status. You can then invite them individually.

---

## Variations

- **Partner lifecycle**: Partners move through statuses: uninvited -> invited -> awaiting_review -> approved. From approved, they can be deactivated or asked to recertify.
- **Partner groups**: You can assign partners to groups during creation or editing to apply item category restrictions and custom reminder schedules.
- **Bulk operations**: CSV import allows you to create many partners at once, but you must invite each one individually.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| A partner says they did not receive the invitation email. | The email may be in spam, or the email address on file is incorrect. | Verify the partner's email address on the edit page and resend the invitation. Ask the partner to check their spam folder. |
| You cannot approve a partner. | The partner may not be in "awaiting review" status. | Check the partner's current status. They must have completed their profile in the partner portal before you can approve them. |
| A deactivated partner wants to become active again. | The partner was deactivated and needs reactivation. | Click the **Reactivate** button on the partner's row in the partners list. |
| CSV import fails. | The CSV file format may not match the expected template. | Download a fresh template, ensure your data matches the column headers, and re-upload. |
