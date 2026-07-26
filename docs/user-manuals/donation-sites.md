# Donation Sites User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization user or admin.

## Overview

Donation Sites represent physical locations where community members can drop off donations for your essentials bank. Managing donation sites lets you track where donations come from and organize your collection points. You can create, edit, deactivate, and import donation sites in bulk via CSV.

---

## Task 1: View All Donation Sites

### Steps

1. In the left sidebar, click **Community** to expand the menu.
2. Click **Donation Sites**.
3. The page displays a table of all donation sites with columns for name, address, and actions.

### Expected Result

You see a list of all active donation sites for your organization.

---

## Task 2: Create a New Donation Site

### Steps

1. Navigate to the **Donation Sites** page by clicking **Community** > **Donation Sites** in the left sidebar.
2. Click the **New Donation Site** button.
3. In the **Name** field, enter the name of the donation site.
4. In the **Address** field, enter the street address of the site.
5. (Optional) Fill in any additional fields displayed on the form (e.g., contact information).
6. Click the **Save** button.

### Expected Result

The donation site is created and appears in the donation sites list. It is now available as a selection when recording donations.

---

## Task 3: Edit a Donation Site

### Steps

1. Navigate to the **Donation Sites** page.
2. Find the donation site you want to edit.
3. Click the **Edit** button in the actions column.
4. Update the **Name**, **Address**, or other fields as needed.
5. Click the **Save** button.

### Expected Result

The donation site information is updated.

---

## Task 4: Deactivate a Donation Site

### Steps

1. Navigate to the **Donation Sites** page.
2. Find the donation site you want to deactivate.
3. Click the **Deactivate** button in the actions column.
4. Confirm the deactivation when prompted.

### Expected Result

The donation site is marked as inactive. It no longer appears as an option when creating new donations, but existing donations linked to this site are preserved. The site can be reactivated later.

---

## Task 5: Reactivate a Donation Site

### Steps

1. Navigate to the **Donation Sites** page.
2. If inactive sites are not visible, look for a filter or option to show inactive sites.
3. Find the deactivated donation site.
4. Click the **Reactivate** button in the actions column.

### Expected Result

The donation site is marked as active again and reappears as an option when creating new donations.

---

## Task 6: Import Donation Sites from CSV

### Steps

1. Navigate to the **Donation Sites** page.
2. Click the **Import Donation Sites** button (available when no sites exist yet).
3. In the CSV import modal, download the CSV template by clicking the template link.
4. Open the template in a spreadsheet program, delete the sample data, and enter your donation site names and addresses.
5. Save the file as a CSV file.
6. Back in the import modal, click **Choose File** and select your CSV file.
7. Click **Upload** to import the data.

### Expected Result

The donation sites from your CSV file are created in the system and appear in the donation sites list.

---

## Variations

- **Inline creation during donations**: When recording a new donation, you can create a new donation site on the fly from the donation form without navigating to the Donation Sites page.
- **Geocoding**: If an address is provided, the system may geocode it for mapping and reporting purposes.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| A donation site does not appear in the dropdown when creating a donation. | The donation site may be deactivated. | Go to **Community** > **Donation Sites** and reactivate the site. |
| CSV import fails with errors. | The CSV file may not match the expected template format. | Download the template again, ensure your data matches the column headers exactly, and re-upload. |
| You cannot delete a donation site. | Donation sites with associated donations cannot be deleted; they can only be deactivated. | Use the **Deactivate** option instead of delete to soft-deactivate the site. |
