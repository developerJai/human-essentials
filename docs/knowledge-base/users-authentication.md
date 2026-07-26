# Users & Authentication

## What is Users & Authentication?

Users & Authentication manages who can access Human Essentials and what they can do. Every person who uses the platform has a user account with a specific role that determines their level of access. The system supports email/password login, Google sign-in, invitation-based onboarding, and password recovery.

## Key Capabilities

- Sign in with email and password or Google account
- Four user roles: Super Admin, Organization Admin, Organization User, and Partner
- Invitation-based onboarding -- new users are invited by email
- Password recovery via email
- Role switching for users who belong to multiple organizations
- Session timeout for security (automatically logs out after extended inactivity)
- User profile management (name, email, password)
- Organization admins can invite, remove, promote, and demote users
- Soft deactivation of users who leave the organization

## How It Works

1. A new user is invited by an admin (organization admin or super admin) via email.
2. The user receives an invitation email with a link to set up their password.
3. After setting up their account, they can log in using their email and password, or via Google sign-in if they have a Google account linked to the same email.
4. Upon login, the system determines the user's role and directs them to the appropriate area:
   - **Super Admins** go to the Admin Dashboard
   - **Organization Admins/Users** go to their organization's Dashboard
   - **Partners** go to the Partner Portal Dashboard
5. If a user belongs to multiple organizations, they can switch between them using the role switcher.
6. Organization admins can manage users from the user management section -- inviting new users, removing users, or changing roles.

## Common Questions

**Q: What are the different user roles?**
A:
- **Super Admin**: Platform-level administrators who manage all organizations, users, and platform settings.
- **Organization Admin**: Manages their organization's settings, users, and can perform all operations including deleting transactions.
- **Organization User**: Day-to-day staff who can record donations, create distributions, and perform standard operations but cannot manage settings or users.
- **Partner**: Users at partner agencies who access the Partner Portal to submit requests and manage their profile.

**Q: How do I invite a new user?**
A: Go to the user management section, enter the new user's email address, and send the invitation. They will receive an email with a link to set up their account.

**Q: What if a user forgets their password?**
A: On the login page, click "Forgot your password?" and enter the account email. A reset link is sent by email. The link is valid for 6 hours.

**Q: Can I sign in with Google?**
A: Yes, if your email address matches an existing account. Google sign-in only works for users who have already been invited and set up -- it does not create new accounts automatically.

**Q: How long before I am automatically logged out?**
A: Sessions expire after 7 days of inactivity. If you are actively using the system, your session stays alive.

**Q: Can a user belong to multiple organizations?**
A: Yes. A user can have roles in multiple organizations and switch between them using the role switcher in the navigation menu.

**Q: How do I remove a user from my organization?**
A: Organization admins can remove users from the user management section. The user loses access to the organization but their historical activity is preserved.

## Tips & Best Practices

- Keep at least two admin users per organization to avoid lockout if one admin leaves.
- Use strong passwords with at least one special character (required by the system).
- Remove users promptly when they leave your organization for security.
- Use the Google sign-in option for convenience if your organization uses Google Workspace.
- Re-invite users after 7 days if they have not accepted their initial invitation.

## Limitations & Important Notes

- Google sign-in only works for existing accounts -- users must be invited first.
- Invitation links expire after 2 weeks. After that, a new invitation must be sent.
- Users cannot re-invite themselves during the first 7 days after an invitation is sent.
- Removing a user does not delete their historical activity (donations, distributions, etc.).
- Passwords must contain at least one special character.

## Related Features

- **Organizations** -- User invitations and role management happen within the organization context
- **Admin Panel** -- Super admins manage all users across the platform
- **Partners** -- Partner users access the system through the Partner Portal
- **Partner Portal** -- The self-service area for partner users
