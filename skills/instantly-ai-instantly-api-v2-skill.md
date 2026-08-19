---
name: Instantly
description: Use when building integrations with Instantly's email outreach platform, automating campaign management, managing email accounts and leads, connecting OAuth accounts, receiving webhook events, or managing workspace operations programmatically.
metadata:
    mintlify-proj: instantly
    version: "1.0"
---

# Instantly API v2 Skill

## Product summary

Instantly API v2 is a REST API for programmatically managing email outreach campaigns, accounts, leads, and workspace operations. Use it to automate campaign workflows, manage email accounts with warmup settings, create and manage lead lists, connect OAuth accounts (Google/Microsoft), receive real-time webhook events, and control multi-workspace operations. The API uses bearer token authentication with scoped API keys and follows REST standards with snake_case field naming. Base URL: `https://api.instantly.ai/api/v2`. Primary docs: https://developer.instantly.ai

## When to use

Reach for this skill when:
- Building integrations that automate email campaign creation, activation, or management
- Programmatically managing email accounts, warmup settings, and sending limits
- Creating or updating lead lists and individual leads in bulk
- Connecting Google Workspace or Microsoft 365 accounts via OAuth
- Setting up webhooks to receive real-time events (email sent, opened, replied, bounced, etc.)
- Retrieving campaign, account, or lead analytics and performance metrics
- Managing workspace members, groups, or billing information
- Migrating from API v1 (which is deprecated in 2025)

## Quick reference

### Authentication
- **Method**: Bearer token in Authorization header
- **Format**: `Authorization: Bearer YOUR_API_KEY`
- **Key creation**: Settings > Integrations > API Keys in Instantly dashboard
- **Scopes**: Select only required scopes when creating keys (e.g., `campaigns:all`, `leads:read`, `accounts:create`)
- **Security**: API keys shown only once; cannot be recovered if lost

### Base URL and Rate Limits
- **Base URL**: `https://api.instantly.ai/api/v2`
- **Rate limits**: 100 requests/second, 6,000 requests/minute (workspace-wide, shared with API v1)
- **Exceeded limit response**: HTTP 429 (Too Many Requests)
- **Mitigation**: Batch requests in groups of 100 with 2-second delays between batches

### Core Resource Endpoints

| Resource | Key Endpoints | Notes |
|----------|---------------|-------|
| **Accounts** | `GET/POST /accounts`, `GET /accounts/{email}`, `POST /accounts/warmup/enable` | Email accounts with warmup config; use email as identifier |
| **Campaigns** | `GET/POST /campaigns`, `GET /campaigns/{id}`, `POST /campaigns/{id}/activate`, `POST /campaigns/{id}/pause` | Email sequences with scheduling; status codes: 0=draft, 1=active, 2=paused, 3=completed, 4=stopped |
| **Leads** | `POST /leads`, `GET /leads` (POST), `PATCH /leads/{id}`, `POST /leads/update-interest-status` | Individual contacts; list endpoint uses POST for complex filters |
| **Lead Lists** | `GET/POST /lead-lists`, `GET /lead-lists/{id}`, `PATCH /lead-lists/{id}` | Collections of leads; can enable auto-enrichment |
| **Webhooks** | `GET/POST /webhooks`, `POST /webhooks/{id}/test`, `GET /webhook-events` | Subscribe to events; test before deploying |
| **OAuth** | `POST /oauth/google/init`, `POST /oauth/microsoft/init`, `GET /oauth/session/status/{sessionId}` | Connect email accounts; sessions expire in 10 minutes |
| **Analytics** | `GET /campaigns/analytics`, `GET /accounts/analytics/daily`, `GET /campaigns/analytics/steps` | Performance metrics; supports date ranges |

### Common Status Codes

| Code | Meaning | Action |
|------|---------|--------|
| 200 | Success | Process response normally |
| 400 | Bad request | Check request body for missing/invalid fields |
| 401 | Unauthorized | Verify API key is valid and not revoked |
| 402 | Payment required | Workspace lacks active paid plan |
| 403 | Forbidden | API key lacks required scope for this operation |
| 404 | Not found | Resource ID doesn't exist or is in wrong workspace |
| 429 | Rate limit exceeded | Reduce request frequency; implement exponential backoff |

### Webhook Event Types

| Category | Events |
|----------|--------|
| **Email** | `email_sent`, `email_opened`, `reply_received`, `auto_reply_received`, `link_clicked`, `email_bounced`, `lead_unsubscribed` |
| **Campaign** | `campaign_completed`, `account_error` |
| **Lead Status** | `lead_interested`, `lead_not_interested`, `lead_neutral`, `lead_closed`, `lead_out_of_office`, `lead_wrong_person` |
| **Meetings** | `lead_meeting_booked`, `lead_meeting_completed` |

## Decision guidance

### When to use POST vs GET for listing
| Scenario | Use |
|----------|-----|
| Simple list with limit/pagination | GET with query params (e.g., `GET /accounts?limit=50`) |
| Complex filters (e.g., leads with multiple conditions) | POST with request body (e.g., `POST /leads` with filter object) |

### Account setup: Manual vs OAuth
| Approach | When to use |
|----------|------------|
| **Manual (IMAP/SMTP)** | You have IMAP/SMTP credentials; full control over account config |
| **OAuth (Google/Microsoft)** | User-initiated connection; better UX; automatic credential refresh |

### Campaign activation: Immediate vs Scheduled
| Approach | When to use |
|----------|------------|
| **Immediate** | `POST /campaigns/{id}/activate` with no schedule override |
| **Scheduled** | Set `campaign_schedule` in campaign object with timezone, days, time windows |

### Webhook event filtering
| Option | When to use |
|--------|------------|
| **All events** | Set `event_type: "all_events"` to catch everything including custom labels |
| **Specific event** | Set `event_type` to single event (e.g., `"reply_received"`) for targeted processing |
| **Custom labels** | Create webhook with `custom_interest_value` matching lead label interest_status |

## Workflow

### 1. Set up API authentication
- Navigate to Instantly dashboard > Settings > Integrations > API Keys
- Click "Create API Key"
- Enter a descriptive name (e.g., "Zapier Integration", "CRM Sync")
- Select only the scopes your integration needs (principle of least privilege)
- Copy the key immediately and store securely (not in code; use environment variables)
- Test with: `curl -H "Authorization: Bearer YOUR_KEY" https://api.instantly.ai/api/v2/accounts?limit=5`

### 2. Create or connect email accounts
**Option A: Manual account (IMAP/SMTP)**
- Gather IMAP/SMTP credentials from email provider
- `POST /accounts` with email, name, provider_code (1=Gmail, 2=Outlook, 3=Custom, etc.), and IMAP/SMTP details
- Optionally enable warmup: `POST /accounts/warmup/enable` with email list

**Option B: OAuth account (Google/Microsoft)**
- `POST /oauth/google/init` or `POST /oauth/microsoft/init` to get auth_url
- Redirect user to auth_url
- Poll `GET /oauth/session/status/{sessionId}` every 2 seconds until status is "success" or "error"
- Account is automatically created on success

### 3. Create a lead list and add leads
- `POST /lead-lists` with name (optionally enable `has_enrichment_task: true`)
- `POST /leads` with email, first_name, last_name, and custom fields
- Or bulk add: `POST /leads/bulk` with array of lead objects
- Verify list: `GET /lead-lists/{id}` and `GET /lead-lists/{id}/verification-stats`

### 4. Create and configure a campaign
- `POST /campaigns` with:
  - `name`: campaign name
  - `sequences[0].steps[]`: array of email steps with delay, variants (A/B test versions)
  - `email_list`: array of sender account emails
  - `campaign_schedule`: timezone, days, time windows
  - `stop_on_reply: true` (optional, stop on first reply)
  - `daily_limit`: max emails per day
- `POST /campaigns/{id}/variables` to add dynamic variables (e.g., {{first_name}})

### 5. Activate campaign and monitor
- `POST /campaigns/{id}/activate` to start sending
- `GET /campaigns/{id}/analytics` to check performance (sent, opened, replied, bounced)
- `GET /campaigns/analytics/steps` to see which email variants perform best
- `POST /campaigns/{id}/pause` to pause; `POST /campaigns/{id}/activate` to resume

### 6. Set up webhooks for real-time events
- `POST /webhooks` with:
  - `target_hook_url`: your endpoint URL
  - `event_type`: specific event or "all_events"
  - `campaign`: (optional) filter to specific campaign
  - `headers`: (optional) custom HTTP headers for authentication
- `POST /webhooks/{id}/test` to send test payload
- Webhook payloads include: timestamp, event_type, workspace, campaign_id, lead_email, step, variant, and event-specific fields
- Implement idempotency: webhook events may retry; use event ID or timestamp to deduplicate

### 7. Retrieve analytics and reports
- `GET /campaigns/analytics?start_date=2024-01-01&end_date=2024-01-31` for campaign metrics
- `GET /accounts/analytics/daily?emails=sender@example.com&start_date=2024-01-01` for daily sending volume
- `GET /campaigns/analytics/steps` to analyze step-level performance
- Date format: YYYY-MM-DD or ISO 8601 timestamp

## Common gotchas

- **API key displayed once only**: Copy immediately after creation. If lost, delete and create a new key.
- **Scope mismatch causes 403**: Verify API key has required scope (e.g., `campaigns:create` to create campaigns). Check error message for required scope.
- **Rate limit applies workspace-wide**: All API keys in the workspace share the 100 req/sec, 6,000 req/min limit. Batch requests with delays.
- **Campaign status codes are numeric**: 0=draft, 1=active, 2=paused, 3=completed, 4=stopped. Don't use string values.
- **Leads endpoint uses POST for listing**: Unlike most REST APIs, `POST /leads` is used for complex filtering. `GET /leads` does not exist.
- **OAuth sessions expire in 10 minutes**: If user doesn't complete OAuth flow within 10 minutes, session expires and you must reinitialize.
- **Webhook retries on failure**: If your endpoint returns non-2xx status, Instantly retries with exponential backoff. Implement idempotency.
- **Email account requires correct provider_code**: Wrong provider_code (1=Gmail, 2=Outlook, etc.) causes account to fail silently. Verify before creating.
- **Campaign sequences array has one element**: Even though `sequences` is an array, only the first element is used. Put all steps in `sequences[0].steps[]`.
- **Warmup is asynchronous**: `POST /accounts/warmup/enable` returns a background job ID. Poll `GET /background-jobs/{id}` to check completion.
- **Custom tracking domain requires CNAME**: If setting `tracking_domain_name`, ensure CNAME is configured. Check status with `GET /accounts/ctd/status?host=yourdomain.com`.
- **Pagination uses cursor, not offset**: Use `starting_after` from previous response's `next_starting_after` field. Don't use page numbers.
- **Webhook payload includes merged lead data**: Extra fields from your lead database may appear in webhook payloads if they were stored in the lead object.
- **API v1 is deprecated**: Plan migration to v2 before 2025. V1 and V2 are incompatible; you need separate API keys.

## Verification checklist

Before submitting integration work:

- [ ] API key created with minimal required scopes (not `all:all`)
- [ ] API key stored in environment variable, not hardcoded
- [ ] Bearer token format correct: `Authorization: Bearer {key}`
- [ ] Base URL is `https://api.instantly.ai/api/v2` (not v1)
- [ ] Rate limit handling implemented: batch requests, 2-second delays between batches
- [ ] Error handling checks HTTP status codes (401, 403, 429, etc.)
- [ ] Campaign `sequences[0].steps[]` array is properly nested (not `sequences[].steps[]`)
- [ ] Campaign status codes are numeric (0, 1, 2, 3, 4), not strings
- [ ] Leads listed via `POST /leads` with filters, not `GET /leads`
- [ ] Webhook test sent and verified: `POST /webhooks/{id}/test`
- [ ] Webhook endpoint returns 2xx status code to prevent retries
- [ ] Webhook idempotency implemented (deduplication by event ID or timestamp)
- [ ] OAuth sessions polled with 2-second intervals, timeout after 10 minutes
- [ ] Analytics date ranges use YYYY-MM-DD or ISO 8601 format
- [ ] Pagination uses `starting_after` cursor, not offset
- [ ] Account warmup jobs monitored via `GET /background-jobs/{id}`
- [ ] Custom tracking domain CNAME verified before use
- [ ] All required fields present in request bodies (check 400 errors)

## Resources

**Comprehensive API reference**: https://developer.instantly.ai/llms.txt

**Critical documentation pages**:
1. [Quickstart](https://developer.instantly.ai/quickstart) — Create API key and send first request
2. [Authorization](https://developer.instantly.ai/getting-started/authorization) — Bearer token setup
3. [Webhook Events Guide](https://developer.instantly.ai/guides/webhook-events) — Event types and payload schema

---

> For additional documentation and navigation, see: https://developer.instantly.ai/llms.txt