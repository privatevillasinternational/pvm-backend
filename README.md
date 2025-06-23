# Private Villas Management (PVM) Backend

A comprehensive vacation rental management system built on Xano platform.

## System Overview

**Platform**: Xano (xhyn-y9xp-avrn.n7c.xano.io)  
**Environment**: Production  
**Current Branch**: v1  
**Total Tables**: 22  
**Last Updated**: June 23, 2025

## Architecture

### Workspaces
- **PVM** (ID: 1) - Main production workspace
- **PVM SAAS** (ID: 2) - SaaS environment
- **PVM SaaS (AI Workspace)** (ID: 4) - AI integration workspace

## Database Schema

### Core Business Tables

#### 🏝️ Properties (ID: 1)
Primary inventory management for vacation rental properties.
- **Created**: October 2, 2023
- **Status**: Active with online tag
- **Authentication**: No

#### 🛏️ Reservations (ID: 5)
Central booking management system.
- **Created**: January 24, 2024
- **Status**: Active with online tag
- **Authentication**: No

#### 💰 Quotes (ID: 29)
Price quotation system for customer inquiries.
- **Created**: November 1, 2024
- **Status**: Active
- **Authentication**: No

#### 📅 Availabilities (ID: 27)
Property availability calendar management.
- **Created**: October 11, 2024
- **Status**: Active with online tag
- **Authentication**: No

### User Management

#### users (ID: 4)
Main user accounts and authentication.
- **Created**: January 22, 2024
- **Authentication**: **Enabled** (auth: true)
- **Tags**: online
- **Note**: Primary authentication table

#### 🌐 peoples (ID: 17)
Extended contact and people management.
- **Created**: April 18, 2024
- **Status**: Active with online tag
- **Authentication**: No

#### 🎯 leads (ID: 6)
Lead generation and prospect tracking.
- **Created**: January 24, 2024
- **Status**: Active
- **Authentication**: No

### Security & Sessions

#### 👤 auth_attempts (ID: 74)
Security monitoring for authentication attempts.
- **Created**: March 3, 2025
- **Authentication**: No

#### 👤 auth_sessions (ID: 75)
Authentication session management.
- **Created**: March 3, 2025
- **Authentication**: No

#### 🖥️ sessions (ID: 25)
General session tracking.
- **Created**: September 5, 2024
- **Authentication**: No

### Payment Processing

#### payments (ID: 137)
Core payment processing records.
- **Created**: April 26, 2025
- **Authentication**: No

#### stripe_users (ID: 32)
Stripe payment platform user integration.
- **Created**: November 26, 2024
- **Authentication**: No

#### stripe_payment_buffer (ID: 33)
Temporary payment processing buffer.
- **Created**: January 11, 2025
- **Authentication**: No

#### currencies (ID: 111)
Multi-currency support system.
- **Created**: March 16, 2025
- **Authentication**: No

### Reservation Management

#### ✅ open_reservations (ID: 28)
Active reservation tracking.
- **Created**: October 14, 2024
- **Authentication**: No
- **Note**: Special characters in name require quotes in queries

#### buffered_reservations (ID: 34)
Temporary reservation processing.
- **Created**: January 13, 2025
- **Authentication**: No

### Marketing & Customer Experience

#### 🤑 discounts (ID: 31)
Discount and promotion management.
- **Created**: November 13, 2024
- **Authentication**: No

#### reviews (ID: 47)
Customer review and feedback system.
- **Created**: February 19, 2025
- **Authentication**: No

#### banners (ID: 121)
Website banner and promotional content.
- **Created**: April 1, 2025
- **Authentication**: No

### Communication System

#### 📁 email_templates (ID: 207)
Email template definitions for demand-based email system.
- **Created**: June 23, 2025
- **Authentication**: No
- **Records**: 29 templates configured
- **Description**: "Email template definitions for demand-based email system"

#### 📨 email_queue (ID: 208)
Email queue and delivery log.
- **Created**: June 23, 2025
- **Authentication**: No
- **Records**: 5 emails currently queued
- **Description**: "Email queue and log for demand-based email system"

### System Support

#### entities (ID: 35)
System entity management.
- **Created**: January 19, 2025
- **Authentication**: No

## Email System

### Template Categories (29 total)

**Guest Communications (15 templates):**
- guest_booking_confirmation
- guest_booking_modification
- guest_booking_cancellation
- new_reservation_request_on_hold
- payment_confirmation
- payment_receipt_invoice
- checkin_instructions
- what_to_pack
- review_request
- review_reminder
- emergency_safety_notification
- seasonal_promotion
- special_offer_coupon
- suggested_stay

**Owner Communications (8 templates):**
- owner_booking_confirmation
- owner_booking_modification
- owner_booking_cancellation
- payout_completed
- payment_receipt_invoice
- monthly_hosting_performance_report
- platform_policy_update
- emergency_safety_notification

**Agency Communications (6 templates):**
- monthly_hosting_performance_report_agency
- platform_policy_update_agency
- emergency_safety_notification_agency
- seasonal_promotion_agency
- special_offer_coupon_agency
- suggested_stay_agency

### Current Queue Status
- **Total queued emails**: 5
- **Status**: All in "queued" state
- **Associated reservations**: IDs 1, 123, 6545
- **Recipients**: Mixed guest and agency emails

## Technical Notes

### Table Naming Conventions
- **Standard tables**: No quotes needed in queries (e.g., `db.query users`)
- **Emoji/special character tables**: Require quotes (e.g., `db.query "🏝️ properties"`)
- **Variable references**: Use underscores for emoji tables (e.g., `$db.____properties`)

### Authentication
- Only `users` table has authentication enabled (auth: true)
- All other tables are open access within the system

### API Endpoints
- Meta API: https://xhyn-y9xp-avrn.n7c.xano.io/api:meta
- Swagger docs: https://xhyn-y9xp-avrn.n7c.xano.io/apispec:meta?type=json

## Development Status

**Active Development Areas:**
- Email system (recently implemented June 23, 2025)
- Payment processing integration
- Multi-currency support

**Stable Components:**
- Core property and reservation management
- User authentication system
- Review and rating system

## Contact

Repository: https://github.com/privatevillasinternational/pvm-backend  
Xano Instance: xhyn-y9xp-avrn.n7c.xano.io