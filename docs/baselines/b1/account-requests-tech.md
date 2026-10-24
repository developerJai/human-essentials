# Account Requests — Technical Documentation

The account-requests feature implements the public-facing registration and admin-side approval pipeline through which a new essentials bank obtains an organization account on Human Essentials. It spans a public (unauthenticated) controller, a super-admin controller, one ActiveRecord model, a mailer with three messages, and the associated views.

## Components

| File | Role |
|---|---|
| `app/controllers/account_requests_controller.rb` | Public request form, email-confirmation flow |
| `app/controllers/admin/account_requests_controller.rb` | Super-admin triage (index, reject, close, for_rejection) |
| `app/models/account_request.rb` | `AccountRequest` model: validations, status enum, JWT tokens, state transitions |
| `app/mailers/account_request_mailer.rb` | `confirmation`, `approval_request`, `rejection` emails |
| `app/views/account_requests/` | `new`, `received`, `confirmation`, `confirm`, `invalid_token` pages |
| `app/views/account_request_mailer/` | HTML + text templates for all three emails |
| `app/views/admin/account_requests/` | `index`, `for_rejection`, `_open_account_request` row partial, `_rejection_modal` |

## Data model

Table `account_requests`:

| Column | Type | Constraints |
|---|---|---|
| `id` | bigint | PK |
| `name` | string | not null |
| `email` | string | not null |
| `organization_name` | string | not null |
| `organization_website` | string | nullable |
| `request_details` | text | not null |
| `status` | string | not null, default `"started"` |
| `rejection_reason` | string | nullable |
| `confirmed_at` | datetime | nullable |
| `ndbn_member_id` | bigint | nullable FK |
| `created_at` / `updated_at` | datetime | not null |

Associations:

```ruby
belongs_to :ndbn_member, class_name: 'NDBNMember', optional: true
has_one :organization, dependent: :nullify
```

The model is versioned with `has_paper_trail`.

### Validations

- `name`: presence.
- `email`: presence, uniqueness, format against `URI::MailTo::EMAIL_REGEXP`.
- `request_details`: presence, `length: { minimum: 50 }`.
- `organization_website`: format against `URI::DEFAULT_PARSER.make_regexp` with message `"should look like 'https://www.example.com'"`, `allow_blank: true`.
- Custom `email_not_already_used_by_organization`: adds `email already used by an existing Organization` if an `Organization` with that email exists and is not the request's own organization.
- Custom `email_not_already_used_by_user`: adds `email already used by an existing User` if a `User` with that email exists and does not belong to the request's organization. Skipped entirely when the request is `rejected` or `admin_closed`.

### Status lifecycle

String-backed enum (value == key):

```ruby
enum :status, %w[started user_confirmed admin_approved rejected admin_closed].map { |v| [v, v] }.to_h
```

- `started` (default) → set at creation.
- `user_confirmed` → set by `confirm!` (also stamps `confirmed_at = Time.current`) and enqueues `AccountRequestMailer.approval_request`.
- `rejected` → set by `reject!(reason)`, stores `rejection_reason`, enqueues `AccountRequestMailer.rejection`.
- `admin_closed` → set by `close!(reason)`; raises `'Cannot be closed from this state'` unless `can_be_closed?` (`started?` or `user_confirmed?`). Also stores the reason in `rejection_reason`. No email is sent on close.
- `admin_approved` → not set anywhere in this feature's files; it is counted as "confirmed" and "closed" by the scopes/predicates below (the approval itself happens in the admin organizations feature, which consumes the request token via `new_admin_organization_url`).

Scopes and predicates:

- `scope :requested` → `status IN (started, user_confirmed)`
- `scope :closed` → `status IN (admin_approved, rejected, admin_closed)`
- `confirmed?` → `user_confirmed? || admin_approved?`
- `processed?` → `organization.present?`
- `can_be_closed?` → `started? || user_confirmed?`

### Identity tokens (JWT)

The public confirmation flow and the admin email links identify a request by a signed token rather than its id:

```ruby
def identity_token
  raise 'must have an id' unless persisted?
  JWT.encode({ account_request_id: id }, Rails.application.secret_key_base, 'HS256')
end
```

`AccountRequest.get_by_identity_token(identity_token)` decodes with HS256 verification against `Rails.application.secret_key_base` and returns the record, or `nil` for any decode/lookup error (rescues `StandardError`). Tokens do not expire.

## Public controller flow

`AccountRequestsController` skips `authorize_user`, `authenticate_user!`, and `require_organization`, and renders in the `devise` layout. Actions: `new`, `create`, `received`, `confirmation`, `confirm`, `invalid_token`.

1. **`new`** — renders the "Essentials Bank Account Request Form". The view first asks the visitor to self-identify via radio buttons as either an *Essentials Bank* or a *Partner Agency*; the partner branch shows only informational links (sign-in page, NDBN member directory, Alliance for Period Supplies directory) because partner accounts are created by their banks, not via this form. The bank branch reveals the form: `name` (autofocus), `email`, `organization_name`, `organization_website` (placeholder `https://www.example.com`), `ndbn_member` association select labelled "NDBN Membership" (options by `full_name`), `request_details` (labelled "Request Details (min 50 characters)"), plus `recaptcha_tags`. On staging (`Rails.env.staging?`) the form is replaced by a card linking to the production form at `https://humanessentials.app/account_requests/new`.
2. **`create`** — strong params permit `:name, :email, :organization_name, :organization_website, :request_details, :ndbn_member_id`. First `verify_recaptcha(model: @account_request)`; on failure flashes `"Invalid captcha submission"` and re-renders `new`. On successful save it enqueues `AccountRequestMailer.confirmation` (`deliver_later`) and redirects to `received_account_requests_path(token: @account_request.identity_token)` with notice `'Account request was successfully created.'`. Validation failure re-renders `new`.
3. **`received`** — "Request Received!" page telling the user an email was sent to their address and to check spam for `no-reply@humanessentials.app`.
4. **`confirmation`** — landing page from the confirmation email ("Are you ready to get started?") with an "I'm ready! Let's go!" link to `confirm`.
5. **`confirm`** — calls `@account_request.confirm!`, which transitions to `user_confirmed` and emails the ops team. The view confirms: "We will be processing your request now" and promises an emailed invitation.
6. **Token guard** — `received`, `confirmation`, and `confirm` run `set_account_request_from_token`: the request is loaded via `get_by_identity_token(params[:token])`; if it is `nil`, already `confirmed?`, or already `processed?`, the user is redirected to `invalid_token_account_requests_path`, which renders "The account request is either invalid, confirmed already, or processed already."

## Admin controller flow

`Admin::AccountRequestsController` inherits from `AdminController` (super-admin only).

- **`index`** — two paginated tables (Kaminari, 15 per page): open requests (`AccountRequest.requested`, newest `created_at` first, page param `open_page`) and closed requests (`AccountRequest.closed`, newest `updated_at` first, page param `close_page`). Open rows show submitted date (`%m/%d/%Y`), organization name/website, request details, titleized status, contact name/email, and two JS buttons: **Reject** and **Close (Admin)**.
- **`_rejection_modal`** — a single shared modal. jQuery wires `.reject-button` clicks to set the form action to `/admin/account_requests/${modal}` (`reject` or `close`), stuff the record id into a hidden `id` field, clear and require `rejection_reason` (client-side guard shows "Reason must be provided" if blank).
- **`reject`** — `@account_request.reject!(reason)`; redirects to the index with notice `"Account request rejected!"`.
- **`close`** — `@account_request.close!(reason)`; notice `"Account request closed!"`. Any raised error (e.g. `'Cannot be closed from this state'`) is rescued and surfaced as an alert.
- **`for_rejection`** — token-based entry point used by the "Reject This Organization" link in the `approval_request` email; renders the single matching request with the same row partial and modal, or "Account Request not found!".

Permitted admin params: `:id, :rejection_reason`.

## Mailers

`AccountRequestMailer < ApplicationMailer`:

| Method | To | Subject |
|---|---|---|
| `confirmation(account_request_id:)` | requester's email | `[Action Required] Human Essential Account Request` |
| `approval_request(account_request_id:)` | `info@humanessentials.app` | `[Account Request] <organization_name>` |
| `rejection(account_request_id:)` | requester's email | `Human Essential Account Request Rejected` |

The confirmation email carries the tokenized confirm link, notes the service is free (supported by Code for Good, servers sponsored by Microsoft), links the User Guide, and shares demo-site credentials for `staging.humanessentials.app` (bank `org_admin1@example.com` / `password!`, partner `verified@example.com` / `password!`; demo data resets daily at 6 AM EST) plus eight getting-started videos. The approval-request email dumps every model attribute into a table and links **Create This Organization** (`new_admin_organization_url(token:)`) and **Reject This Organization** (`for_rejection_admin_account_requests_url(token:)`). The rejection email includes `rejection_reason` verbatim. All sends use `deliver_later`.

## Caveats

- Demo credentials and the token are embedded in outbound email; JWTs are non-expiring, but the token guard rejects reuse once the request is confirmed or processed.
- `close!` emails nothing — a closed requester is never notified, unlike a rejected one.
- The uniqueness checks against existing `Organization`/`User` emails mean a rejected/closed request's email can be reused later (the user-email check is skipped for terminal rejected/closed states).
- Approval is not implemented in this controller; `admin_approved` is reached via the admin organizations creation flow consuming the same identity token.
