# Database Schema Reference

## Table Overview
Total tables: 22  
Authentication enabled: 1 table (users)  
Emoji/special character tables: 14 tables

## Standard Tables (No Quotes Required)

### banners (ID: 121)
- **Created**: April 1, 2025
- **Updated**: June 5, 2025
- **Auth**: No
- **Query**: `db.query banners`

### buffered_reservations (ID: 34)
- **Created**: January 13, 2025
- **Updated**: March 9, 2025
- **Auth**: No
- **Query**: `db.query buffered_reservations`

### currencies (ID: 111)
- **Created**: March 16, 2025
- **Updated**: March 16, 2025
- **Auth**: No
- **Query**: `db.query currencies`

### entities (ID: 35)
- **Created**: January 19, 2025
- **Updated**: June 17, 2025
- **Auth**: No
- **Query**: `db.query entities`

### payments (ID: 137)
- **Created**: April 26, 2025
- **Updated**: April 28, 2025
- **Auth**: No
- **Query**: `db.query payments`

### reviews (ID: 47)
- **Created**: February 19, 2025
- **Updated**: June 5, 2025
- **Auth**: No
- **Query**: `db.query reviews`

### stripe_payment_buffer (ID: 33)
- **Created**: January 11, 2025
- **Updated**: March 8, 2025
- **Auth**: No
- **Query**: `db.query stripe_payment_buffer`

### stripe_users (ID: 32)
- **Created**: November 26, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Query**: `db.query stripe_users`

### users (ID: 4)
- **Created**: January 22, 2024
- **Updated**: June 5, 2025
- **Auth**: **YES** (auth: true)
- **Tags**: online
- **Query**: `db.query users`
- **Note**: Primary authentication table

## Emoji/Special Character Tables (Quotes Required)

### ✅ open_reservations (ID: 28)
- **Created**: October 14, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Query**: `db.query "✅ open_reservations"`
- **Variable**: `$db.__open_reservations`

### 🌐 peoples (ID: 17)
- **Created**: April 18, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Tags**: online
- **Query**: `db.query "🌐 peoples"`
- **Variable**: `$db.___peoples`

### 🎯 leads (ID: 6)
- **Created**: January 24, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Query**: `db.query "🎯 leads"`
- **Variable**: `$db.___leads`

### 🏝️ properties (ID: 1)
- **Created**: October 2, 2023
- **Updated**: June 12, 2025
- **Auth**: No
- **Tags**: online
- **Query**: `db.query "🏝️ properties"`
- **Variable**: `$db.____properties`
- **Note**: Primary property inventory table

### 👤 auth_attempts (ID: 74)
- **Created**: March 3, 2025
- **Updated**: March 3, 2025
- **Auth**: No
- **Query**: `db.query "👤 auth_attempts"`
- **Variable**: `$db.___auth_attempts`

### 👤 auth_sessions (ID: 75)
- **Created**: March 3, 2025
- **Updated**: March 3, 2025
- **Auth**: No
- **Query**: `db.query "👤 auth_sessions"`
- **Variable**: `$db.___auth_sessions`

### 💰 quotes (ID: 29)
- **Created**: November 1, 2024
- **Updated**: June 6, 2025
- **Auth**: No
- **Query**: `db.query "💰 quotes"`
- **Variable**: `$db.___quotes`

### 📁 email_templates (ID: 207)
- **Created**: June 23, 2025
- **Updated**: June 23, 2025
- **Auth**: No
- **Records**: 29
- **Query**: `db.query "📁 email_templates"`
- **Variable**: `$db.___email_templates`
- **Description**: Email template definitions for demand-based email system

### 📅 availabilities (ID: 27)
- **Created**: October 11, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Tags**: online
- **Query**: `db.query "📅 availabilities"`
- **Variable**: `$db.___availabilities`

### 📨 email_queue (ID: 208)
- **Created**: June 23, 2025
- **Updated**: June 23, 2025
- **Auth**: No
- **Records**: 5
- **Query**: `db.query "📨 email_queue"`
- **Variable**: `$db.___email_queue`
- **Description**: Email queue and log for demand-based email system

### 🖥️ sessions (ID: 25)
- **Created**: September 5, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Query**: `db.query "🖥️ sessions"`
- **Variable**: `$db.____sessions`

### 🛏️ reservations (ID: 5)
- **Created**: January 24, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Tags**: online
- **Query**: `db.query "🛏️ reservations"`
- **Variable**: `$db.____reservations`
- **Note**: Central booking management

### 🤑 discounts (ID: 31)
- **Created**: November 13, 2024
- **Updated**: June 5, 2025
- **Auth**: No
- **Query**: `db.query "🤑 discounts"`
- **Variable**: `$db.___discounts`

## Query Syntax Guide

### Standard Tables
```xano
// Simple query
db.query users

// With conditions
db.query users where id = 123

// Variable reference
$db.users
```

### Emoji/Special Character Tables
```xano
// Quoted table name required
db.query "🏝️ properties"

// With conditions
db.query "🏝️ properties" where status = "active"

// Variable reference (underscores replace special chars)
$db.____properties
```

### Sorting Examples
```xano
// Standard table
sort = "users.created_at"

// Emoji table
sort = "🏝️ properties.created_at"
```

## Authentication Configuration

Only the `users` table has authentication enabled:
- **Table**: users (ID: 4)
- **Auth Setting**: true
- **Purpose**: Primary user authentication
- **Required for**: JWT token generation, login endpoints

All other tables operate without authentication requirements within the Xano system.

## Workspace Configuration

### Current Workspace: PVM (ID: 1)
- **Branch**: v1
- **Environment**: Production
- **Total Tables**: 22

### Related Workspaces
- **PVM SAAS** (ID: 2) - SaaS environment
- **PVM SaaS (AI Workspace)** (ID: 4) - AI integration

## API Access

### Meta API Endpoints
- **Base**: https://xhyn-y9xp-avrn.n7c.xano.io/api:meta
- **Swagger**: https://xhyn-y9xp-avrn.n7c.xano.io/apispec:meta?type=json

### Rate Limiting
- **Status**: Not applied to current instance
- **Monitoring**: Available through instance configuration