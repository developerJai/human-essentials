# Partner Groups User Manual

## Prerequisites

- You must be logged in to Human Essentials as an organization admin.
- At least one partner agency must exist.
- At least one item category must exist if you want to restrict item access by group.

## Overview

Partner Groups let you organize partner agencies into logical groups for easier management. You can assign item category restrictions to a group, controlling which types of items partners in that group can request. You can also set custom reminder schedules for groups to send deadline reminders at different intervals. Groups appear as a tab on the Partner Agencies page.

---

## Task 1: View All Partner Groups

### Steps

1. In the left sidebar, click **Partner Agencies** to expand the menu.
2. Click **All Partners**.
3. On the **Partner Agencies** page, click the **Groups** tab.
4. The table shows all partner groups with their names, number of partners, and item category restrictions.

### Expected Result

You see a list of all partner groups for your organization.

---

## Task 2: Create a New Partner Group

### Steps

1. Navigate to the **Partner Agencies** page and click the **Groups** tab.
2. Click the **New Partner Group** button.
3. In the **Name** field, enter a descriptive name for the group (e.g., "Shelters" or "Schools").
4. (Optional) Select one or more **Item Categories** to restrict which item types partners in this group can request. If left blank, partners in the group can request any item.
5. (Optional) Configure a custom **Reminder Schedule** for the group's deadline reminders.
6. Select the partners to include in this group by checking them in the partner list.
7. Click the **Save** button.

### Expected Result

The partner group is created and the selected partners are assigned to it. If item category restrictions were set, those partners can only request items from the allowed categories.

---

## Task 3: Edit a Partner Group

### Steps

1. Navigate to the **Partner Agencies** page and click the **Groups** tab.
2. Find the group you want to edit.
3. Click the **Edit** button for that group.
4. Update the **Name**, **Item Categories**, **Reminder Schedule**, or partner membership as needed.
5. Click the **Save** button.

### Expected Result

The partner group is updated. Changes to item category restrictions take effect immediately for future partner requests.

---

## Task 4: Delete a Partner Group

### Steps

1. Navigate to the **Partner Agencies** page and click the **Groups** tab.
2. Find the group you want to delete.
3. Click the **Delete** button for that group.
4. Confirm the deletion when prompted.

### Expected Result

The partner group is removed. Partners that were in the group are not deleted; they simply no longer belong to that group and revert to having no group-level item restrictions.

---

## Variations

- **No item restrictions**: If you create a group without item category restrictions, it serves only as an organizational label and for reminder scheduling purposes.
- **Multiple groups**: A partner can belong to only one group at a time. Assigning a partner to a new group removes them from their previous group.
- **Custom reminder schedules**: Groups can have different reminder schedules, allowing you to send more frequent reminders to certain partners.

---

## Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| A partner in a group cannot request certain items. | The group has item category restrictions that exclude those items. | Edit the partner group and add the missing item categories, or move the partner to a different group. |
| You cannot find the **Groups** tab. | You may not have organization admin permissions. | The Groups tab is available to all users on the Partner Agencies page. Ensure you are on the correct page. |
| Deleting a group does not delete the partners. | Groups are organizational labels; deleting a group only removes the grouping, not the partners. | This is expected behavior. Partners remain in the system after their group is deleted. |
