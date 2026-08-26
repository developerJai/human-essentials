# Feature Catalog -- Human Essentials

> **Project:** https://github.com/rubyforgood/human-essentials
> **Generated:** 2026-06-13T00:00:00Z
> **Features:** 28

---

## Features

| # | Feature | Description | Key Files |
|---|---------|-------------|-----------|
| 1 | donations | Manage incoming donations of supplies from drives, sites, and manufacturers | 12 files |
| 2 | distributions | Manage outgoing distributions of supplies to partner organizations | 20 files |
| 3 | purchases | Track purchases of supplies from vendors | 9 files |
| 4 | transfers | Transfer inventory between storage locations | 8 files |
| 5 | requests | Manage requests from partners for supplies (bank-side view) | 15 files |
| 6 | adjustments | Create manual inventory adjustments at storage locations | 6 files |
| 7 | audits | Audit inventory at storage locations to verify physical counts | 5 files |
| 8 | items | Manage item types, categories, units, and line items | 12 files |
| 9 | kits | Bundle items into reusable kits with allocation to storage locations | 7 files |
| 10 | barcode-items | Scan and manage barcode lookups for items | 3 files |
| 11 | storage-locations | Manage storage locations and their inventory levels | 8 files |
| 12 | partners | Manage partner organizations from the bank side (invite, approve, deactivate) | 18 files |
| 13 | partner-groups | Group partners for item sharing and request configuration | 3 files |
| 14 | partner-portal | Partner-facing portal for requests, families, children, profiles, and distributions | 28 files |
| 15 | product-drives | Organize and track product donation drives and participants | 9 files |
| 16 | donation-sites | Manage donation drop-off site locations | 3 files |
| 17 | manufacturers | Manage manufacturer records for donated goods | 3 files |
| 18 | vendors | Manage vendor records for purchased goods | 3 files |
| 19 | organizations | Organization settings and user management within an org | 7 files |
| 20 | users-authentication | User accounts, Devise authentication, roles, and invitations | 18 files |
| 21 | reports | Summary reports, itemized reports, and annual reports | 14 files |
| 22 | historical-trends | Historical trend charts for distributions, purchases, and donations | 6 files |
| 23 | dashboard | Organization dashboard with summary statistics and low inventory alerts | 6 files |
| 24 | admin-panel | Super admin panel for managing orgs, users, base items, and NDBN members | 14 files |
| 25 | broadcast-announcements | System-wide broadcast announcements | 5 files |
| 26 | account-requests | New organization account registration and approval requests | 7 files |
| 27 | static-pages | Static marketing pages, help page, and privacy policy | 4 files |
| 28 | inventory-events | Core event-sourcing infrastructure for inventory tracking | 14 files |

---

## File-to-Feature Mapping

```yaml
# PATTERNS:
#   - path/to/dir/          -> matches any file under that directory (recursive)
#   - path/to/prefix_*      -> glob wildcard, matches files with that prefix
#   - path/to/exact_file.rb -> exact file match

donations:
  - app/controllers/donations_controller.rb
  - app/models/donation.rb
  - app/models/view/donations.rb
  - app/services/donation_create_service.rb
  - app/services/donation_destroy_service.rb
  - app/services/donation_itemized_breakdown_service.rb
  - app/services/exports/export_donations_csv_service.rb
  - app/events/donation_event.rb
  - app/events/donation_destroy_event.rb
  - app/helpers/donations_helper.rb
  - app/pdfs/donation_pdf.rb
  - app/views/donations/

distributions:
  - app/controllers/distributions_controller.rb
  - app/controllers/distributions_by_county_controller.rb
  - app/models/distribution.rb
  - app/services/distribution_create_service.rb
  - app/services/distribution_destroy_service.rb
  - app/services/distribution_update_service.rb
  - app/services/distribution_content_change_service.rb
  - app/services/distribution_service.rb
  - app/services/distribution_totals_service.rb
  - app/services/distribution_itemized_breakdown_service.rb
  - app/services/calendar_service.rb
  - app/services/deadline_service.rb
  - app/services/exports/export_distributions_csv_service.rb
  - app/events/distribution_event.rb
  - app/events/distribution_destroy_event.rb
  - app/helpers/distribution_helper.rb
  - app/mailers/distribution_mailer.rb
  - app/pdfs/distribution_pdf.rb
  - app/queries/distribution_summary_by_county_query.rb
  - app/views/distributions/
  - app/views/distributions_by_county/
  - app/views/distribution_mailer/

purchases:
  - app/controllers/purchases_controller.rb
  - app/models/purchase.rb
  - app/services/purchase_create_service.rb
  - app/services/purchase_destroy_service.rb
  - app/services/exports/export_purchases_csv_service.rb
  - app/events/purchase_event.rb
  - app/events/purchase_destroy_event.rb
  - app/helpers/purchases_helper.rb
  - app/views/purchases/

transfers:
  - app/controllers/transfers_controller.rb
  - app/models/transfer.rb
  - app/services/transfer_create_service.rb
  - app/services/transfer_destroy_service.rb
  - app/services/exports/export_transfers_csv_service.rb
  - app/events/transfer_event.rb
  - app/events/transfer_destroy_event.rb
  - app/views/transfers/

requests:
  - app/controllers/requests_controller.rb
  - app/controllers/requests/cancelation_controller.rb
  - app/models/request.rb
  - app/models/request_item.rb
  - app/models/view/request_info.rb
  - app/models/view/requests.rb
  - app/services/request_destroy_service.rb
  - app/services/request_itemized_breakdown_service.rb
  - app/services/requests_total_items_service.rb
  - app/services/exports/export_request_service.rb
  - app/helpers/requests_helper.rb
  - app/mailers/request_mailer.rb
  - app/mailers/requests_confirmation_mailer.rb
  - app/pdfs/picklists_pdf.rb
  - app/views/requests/
  - app/views/request_mailer/
  - app/views/requests_confirmation_mailer/

adjustments:
  - app/controllers/adjustments_controller.rb
  - app/models/adjustment.rb
  - app/services/adjustment_create_service.rb
  - app/services/exports/export_adjustments_csv_service.rb
  - app/events/adjustment_event.rb
  - app/views/adjustments/

audits:
  - app/controllers/audits_controller.rb
  - app/models/audit.rb
  - app/events/audit_event.rb
  - app/events/event_types/audit_payload.rb
  - app/views/audits/

items:
  - app/controllers/items_controller.rb
  - app/controllers/item_categories_controller.rb
  - app/models/item.rb
  - app/models/item_category.rb
  - app/models/item_unit.rb
  - app/models/unit.rb
  - app/models/line_item.rb
  - app/services/item_create_service.rb
  - app/helpers/items_helper.rb
  - app/views/items/
  - app/views/item_categories/
  - app/views/line_items/

kits:
  - app/controllers/kits_controller.rb
  - app/models/kit.rb
  - app/services/kit_create_service.rb
  - app/events/kit_allocate_event.rb
  - app/events/kit_deallocate_event.rb
  - app/helpers/kits_helper.rb
  - app/views/kits/

barcode-items:
  - app/controllers/barcode_items_controller.rb
  - app/models/barcode_item.rb
  - app/views/barcode_items/

storage-locations:
  - app/controllers/storage_locations_controller.rb
  - app/models/storage_location.rb
  - app/models/inventory_item.rb
  - app/models/view/inventory.rb
  - app/services/storage_location_deactivate_service.rb
  - app/services/inventory_check_service.rb
  - app/queries/items_by_storage_collection_and_quantity_query.rb
  - app/queries/low_inventory_query.rb
  - app/views/storage_locations/

partners:
  - app/controllers/partners_controller.rb
  - app/controllers/partner_users_controller.rb
  - app/controllers/admin/partners_controller.rb
  - app/models/partner.rb
  - app/services/partner_create_service.rb
  - app/services/partner_invite_service.rb
  - app/services/partner_approval_service.rb
  - app/services/partner_deactivate_service.rb
  - app/services/partner_reactivate_service.rb
  - app/services/partner_profile_update_service.rb
  - app/services/partner_request_recertification_service.rb
  - app/services/exports/export_partners_csv_service.rb
  - app/helpers/partners_helper.rb
  - app/mailers/partner_mailer.rb
  - app/jobs/partner_mailer_job.rb
  - app/jobs/notify_partner_job.rb
  - app/views/partners/
  - app/views/partner_users/
  - app/views/partner_mailer/
  - app/views/admin/partners/

partner-groups:
  - app/controllers/partner_groups_controller.rb
  - app/models/partner_group.rb
  - app/views/partner_groups/

partner-portal:
  - app/controllers/partners/base_controller.rb
  - app/controllers/partners/dashboards_controller.rb
  - app/controllers/partners/requests_controller.rb
  - app/controllers/partners/individuals_requests_controller.rb
  - app/controllers/partners/family_requests_controller.rb
  - app/controllers/partners/families_controller.rb
  - app/controllers/partners/children_controller.rb
  - app/controllers/partners/authorized_family_members_controller.rb
  - app/controllers/partners/profiles_controller.rb
  - app/controllers/partners/users_controller.rb
  - app/controllers/partners/helps_controller.rb
  - app/controllers/partners/approval_requests_controller.rb
  - app/controllers/partners/recertification_requests_controller.rb
  - app/controllers/partners/distributions_controller.rb
  - app/models/partners/base.rb
  - app/models/partners/family.rb
  - app/models/partners/child.rb
  - app/models/partners/authorized_family_member.rb
  - app/models/partners/profile.rb
  - app/models/partners/family_request.rb
  - app/models/partners/item_request.rb
  - app/models/partners/child_item_request.rb
  - app/models/partners/served_area.rb
  - app/services/partners/family_request_create_service.rb
  - app/services/partners/request_create_service.rb
  - app/services/partners/request_approval_service.rb
  - app/services/partners/fetch_partners_to_remind_now_service.rb
  - app/services/partners/section_error_service.rb
  - app/services/partners/update_family.rb
  - app/services/partner_fetch_requestable_items_service.rb
  - app/helpers/partners/profile_helper.rb
  - app/helpers/partners/sortable_helper.rb
  - app/views/partners/dashboards/
  - app/views/partners/requests/
  - app/views/partners/individuals_requests/
  - app/views/partners/family_requests/
  - app/views/partners/families/
  - app/views/partners/children/
  - app/views/partners/authorized_family_members/
  - app/views/partners/profiles/
  - app/views/partners/users/
  - app/views/partners/helps/
  - app/views/partners/distributions/
  - app/views/served_areas/

product-drives:
  - app/controllers/product_drives_controller.rb
  - app/controllers/product_drive_participants_controller.rb
  - app/models/product_drive.rb
  - app/models/product_drive_participant.rb
  - app/services/product_drive_summary_service.rb
  - app/services/exports/export_product_drives_csv_service.rb
  - app/helpers/product_drive_helper.rb
  - app/views/product_drives/
  - app/views/product_drive_participants/

donation-sites:
  - app/controllers/donation_sites_controller.rb
  - app/models/donation_site.rb
  - app/views/donation_sites/

manufacturers:
  - app/controllers/manufacturers_controller.rb
  - app/models/manufacturer.rb
  - app/views/manufacturers/

vendors:
  - app/controllers/vendors_controller.rb
  - app/models/vendor.rb
  - app/views/vendors/

organizations:
  - app/controllers/organizations_controller.rb
  - app/models/organization.rb
  - app/models/organization_stats.rb
  - app/services/organization_update_service.rb
  - app/helpers/organization_helper.rb
  - app/mailers/organization_mailer.rb
  - app/views/organizations/
  - app/views/organization_mailer/

users-authentication:
  - app/controllers/users_controller.rb
  - app/controllers/users/sessions_controller.rb
  - app/controllers/users/registrations_controller.rb
  - app/controllers/users/passwords_controller.rb
  - app/controllers/users/confirmations_controller.rb
  - app/controllers/users/invitations_controller.rb
  - app/controllers/users/omniauth_callbacks_controller.rb
  - app/controllers/users/unlocks_controller.rb
  - app/controllers/profiles_controller.rb
  - app/models/user.rb
  - app/models/role.rb
  - app/models/users_role.rb
  - app/services/user_invite_service.rb
  - app/services/add_role_service.rb
  - app/services/remove_role_service.rb
  - app/mailers/custom_devise_mailer.rb
  - app/mailers/user_mailer.rb
  - app/helpers/users_helper.rb
  - app/views/users/
  - app/views/profiles/
  - app/views/user_mailer/

reports:
  - app/controllers/reports_controller.rb
  - app/controllers/reports/annual_reports_controller.rb
  - app/models/annual_report.rb
  - app/services/reports.rb
  - app/services/reports/summary_report_service.rb
  - app/services/reports/diaper_report_service.rb
  - app/services/reports/children_served_report_service.rb
  - app/services/reports/adult_incontinence_report_service.rb
  - app/services/reports/period_supply_report_service.rb
  - app/services/reports/other_products_report_service.rb
  - app/services/reports/partner_info_report_service.rb
  - app/services/reports/warehouse_report_service.rb
  - app/services/exports/export_report_csv_service.rb
  - app/views/reports/

historical-trends:
  - app/controllers/historical_trends/base_controller.rb
  - app/controllers/historical_trends/distributions_controller.rb
  - app/controllers/historical_trends/purchases_controller.rb
  - app/controllers/historical_trends/donations_controller.rb
  - app/services/historical_trend_service.rb
  - app/helpers/historical_trends_helper.rb
  - app/views/historical_trends/

dashboard:
  - app/controllers/dashboard_controller.rb
  - app/helpers/dashboard_helper.rb
  - app/queries/items_in_query.rb
  - app/queries/items_in_total_query.rb
  - app/queries/items_out_query.rb
  - app/queries/items_out_total_query.rb
  - app/views/dashboard/

admin-panel:
  - app/controllers/admin_controller.rb
  - app/controllers/admin/organizations_controller.rb
  - app/controllers/admin/users_controller.rb
  - app/controllers/admin/base_items_controller.rb
  - app/controllers/admin/barcode_items_controller.rb
  - app/controllers/admin/ndbn_members_controller.rb
  - app/controllers/admin/questions_controller.rb
  - app/models/base_item.rb
  - app/models/ndbn_member.rb
  - app/models/question.rb
  - app/services/sync_ndbn_members.rb
  - app/views/admin/dashboard.html.erb
  - app/views/admin/organizations/
  - app/views/admin/users/
  - app/views/admin/base_items/
  - app/views/admin/barcode_items/
  - app/views/admin/ndbn_members/
  - app/views/admin/questions/

broadcast-announcements:
  - app/controllers/broadcast_announcements_controller.rb
  - app/controllers/admin/broadcast_announcements_controller.rb
  - app/models/broadcast_announcement.rb
  - app/views/broadcast_announcements/
  - app/views/admin/broadcast_announcements/

account-requests:
  - app/controllers/account_requests_controller.rb
  - app/controllers/admin/account_requests_controller.rb
  - app/models/account_request.rb
  - app/mailers/account_request_mailer.rb
  - app/views/account_requests/
  - app/views/account_request_mailer/
  - app/views/admin/account_requests/

static-pages:
  - app/controllers/static_controller.rb
  - app/controllers/help_controller.rb
  - app/views/static/
  - app/views/help/

inventory-events:
  - app/models/event.rb
  - app/controllers/events_controller.rb
  - app/events/inventory_aggregate.rb
  - app/events/inventory_error.rb
  - app/events/inventory_action_error.rb
  - app/events/snapshot_event.rb
  - app/events/update_existing_event.rb
  - app/events/event_types/inventory.rb
  - app/events/event_types/inventory_payload.rb
  - app/events/event_types/event_item.rb
  - app/events/event_types/event_line_item.rb
  - app/events/event_types/event_storage_location.rb
  - app/events/event_types/struct_coder.rb
  - app/views/events/
```

---

## Coverage

- **Controllers mapped:** 65 / 65 (excluding application_controller.rb and shared concerns)
- **Models mapped:** 49 / 49 (excluding ApplicationRecord and shared concerns)
- **Services mapped:** 60 / 64 (excluding shared utilities)
- **Events mapped:** 24 / 24
- **Jobs mapped:** 3 / 3 (excluding application_job.rb and infrastructure jobs)
- **Mailers mapped:** 9 / 9 (excluding application_mailer.rb)
- **Helpers mapped:** 17 / 17 (excluding application_helper.rb and shared utilities)
- **Queries mapped:** 7 / 7
- **PDFs mapped:** 3 / 3

### Unmapped files (shared infrastructure -- intentionally excluded)

- `app/controllers/application_controller.rb` -- base controller
- `app/controllers/concerns/importable.rb` -- shared CSV import concern
- `app/controllers/concerns/validatable.rb` -- shared validation concern
- `app/controllers/attachments_controller.rb` -- generic ActiveStorage attachment deletion
- `app/models/application_record.rb` -- base model
- `app/models/concerns/exportable.rb` -- shared export concern
- `app/models/concerns/filterable.rb` -- shared filter concern
- `app/models/concerns/geocodable.rb` -- shared geocoding concern
- `app/models/concerns/issued_at.rb` -- shared timestamp concern
- `app/models/concerns/item_quantity.rb` -- shared quantity concern
- `app/models/concerns/itemizable.rb` -- shared line item concern
- `app/models/concerns/provideable.rb` -- shared concern
- `app/models/concerns/taggable.rb` -- shared tagging concern
- `app/models/concerns/valuable.rb` -- shared valuation concern
- `app/models/errors.rb` -- shared error classes
- `app/models/result.rb` -- shared Result monad
- `app/models/option.rb` -- shared option/select helper
- `app/models/county.rb` -- shared geographic reference data
- `app/models/tag.rb` -- shared tagging infrastructure
- `app/models/tagging.rb` -- shared tagging join model
- `app/mailers/application_mailer.rb` -- base mailer
- `app/mailers/reminder_deadline_mailer.rb` -- shared reminder mailer
- `app/jobs/application_job.rb` -- base job
- `app/jobs/backup_db_rds.rb` -- infrastructure backup job
- `app/jobs/historical_data_cache_job.rb` -- infrastructure caching job
- `app/jobs/reminder_deadline_job.rb` -- shared reminder job
- `app/services/service_object_errors_mixin.rb` -- shared service concern
- `app/services/itemizable_update_service.rb` -- shared service used by multiple features
- `app/services/text_interpolator_service.rb` -- shared text utility
- `app/services/reminder_schedule_service.rb` -- shared reminder scheduling
- `app/helpers/application_helper.rb` -- shared helper
- `app/helpers/address_helper.rb` -- shared helper
- `app/helpers/date_helper.rb` -- shared helper
- `app/helpers/date_range_helper.rb` -- shared helper
- `app/helpers/filter_helper.rb` -- shared helper
- `app/helpers/icon_helper.rb` -- shared helper
- `app/helpers/ui_helper.rb` -- shared helper
- `app/views/layouts/` -- shared layout templates
- `app/views/shared/` -- shared view partials
- `app/views/kaminari/` -- pagination partials (gem override)
- `app/views/errors/` -- error pages
- `app/views/active_storage/` -- Active Storage views (framework)
