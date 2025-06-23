# Email System Documentation

## Overview
The PVM email system implements a demand-based architecture where emails are triggered by specific business events and queued for delivery.

## Schema Details

### 📁 email_templates Table (ID: 207)
**Purpose**: Template definitions for all email types  
**Created**: June 23, 2025  
**Records**: 29 configured templates

#### Fields
- `id` (int, required) - Primary key
- `created_at` (timestamp, auto) - Creation timestamp
- `demand` (text, required) - Event type trigger (e.g., "guest_booking_confirmation")
- `template_id` (text, optional) - External template reference (currently null)
- `destination` (text, required) - Recipient type (guest/owner/agency)
- `description` (text, required) - Human-readable template description

### 📨 email_queue Table (ID: 208)
**Purpose**: Email delivery queue and processing log  
**Created**: June 23, 2025  
**Records**: 5 emails currently queued

#### Fields
- `id` (int, required) - Primary key
- `created_at` (timestamp, auto) - Queue entry timestamp
- `demand` (text, required) - Event type that triggered email
- `reservation_id` (int, optional) - Associated reservation
- `recipient_email` (email, required) - Delivery address
- `dynamic_data` (json, required) - Template variables and context
- `status` (enum, required) - Processing status (default: "queued")
- `attempt_count` (int, required) - Delivery attempt counter (default: 0)
- `last_attempt_at` (timestamp, optional) - Last delivery attempt

## Email Categories

### Guest Communications (15 templates)
Emails sent directly to vacation rental guests:

1. **guest_booking_confirmation** - Post-booking confirmation
2. **guest_booking_modification** - Booking change notifications
3. **guest_booking_cancellation** - Cancellation confirmations
4. **new_reservation_request_on_hold** - Pending request notifications
5. **payment_confirmation** - Payment processing confirmations
6. **payment_receipt_invoice** - Payment receipts and invoices
7. **checkin_instructions** - Pre-arrival instructions
8. **what_to_pack** - Packing recommendations
9. **review_request** - Initial review requests
10. **review_reminder** - Follow-up review reminders
11. **emergency_safety_notification** - Safety alerts
12. **seasonal_promotion** - Seasonal marketing campaigns
13. **special_offer_coupon** - Discount offerings
14. **suggested_stay** - Personalized recommendations

### Owner Communications (8 templates)
Emails sent to property owners:

1. **owner_booking_confirmation** - Booking notifications
2. **owner_booking_modification** - Change notifications
3. **owner_booking_cancellation** - Cancellation notifications
4. **payout_completed** - Payment notifications
5. **payment_receipt_invoice** - Owner earnings receipts
6. **monthly_hosting_performance_report** - Performance analytics
7. **platform_policy_update** - Policy change notifications
8. **emergency_safety_notification** - Safety alerts

### Agency Communications (6 templates)
Emails sent to agency partners:

1. **monthly_hosting_performance_report_agency** - Agency performance reports
2. **platform_policy_update_agency** - Agency-specific policy updates
3. **emergency_safety_notification_agency** - Emergency notifications
4. **seasonal_promotion_agency** - Agency promotional campaigns
5. **special_offer_coupon_agency** - Agency discount distributions
6. **suggested_stay_agency** - Client recommendations

## Current Queue Analysis

### Queue Status (as of June 23, 2025)
**Total emails queued**: 5  
**Processing status**: All "queued" (not yet processed)  
**Attempt count**: 0 for all emails (no delivery attempts)

### Queued Email Breakdown
1. **ID 1**: guest_booking_confirmation for reservation 123
2. **ID 2**: guest_booking_confirmation for reservation 123 (duplicate)
3. **ID 3**: guest_booking_confirmation for reservation 6545
4. **ID 4**: monthly_hosting_performance_report_agency for reservation 6545
5. **ID 5**: guest_booking_confirmation for reservation 1 (test email)

### Recipients
- guest@example.com (3 emails)
- razea@eaze.com (1 email)
- test@example.com (1 email)

## Technical Implementation Notes

### Dynamic Data Structure
Each queued email contains a `dynamic_data` JSON field with:
- `demand` - Email type
- `recipient` - Target email address
- `destination` - Recipient category
- `reservation_id` - Associated booking
- `validation_passed` - Processing validation status
- `reservation_details` - Full booking context (when available)

### Status Values
The `status` enum field tracks email processing:
- **queued** - Ready for delivery (current state for all emails)
- Additional status values not yet observed in current data

### Integration Points
- **Reservation System**: Emails triggered by booking events
- **Payment System**: Payment confirmations and receipts
- **Review System**: Post-stay feedback requests
- **Analytics**: Performance reporting for owners/agencies

## Development Status
- ✅ Template definitions configured
- ✅ Queue mechanism implemented
- ⏳ Template content integration pending (template_id currently null)
- ⏳ Delivery mechanism pending (all emails in queued state)
- ⏳ Retry logic pending (no delivery attempts recorded)