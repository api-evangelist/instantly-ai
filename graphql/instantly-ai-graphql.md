# Instantly GraphQL Schema

## Overview

This conceptual GraphQL schema models the Instantly cold email outreach and sales acceleration platform. Instantly provides mailbox sending infrastructure, email warmup, a B2B lead database, deliverability tools, and a unified inbox for replies via the v2 REST API at `api.instantly.ai/api/v2`.

The schema covers the full domain surface: campaigns and sequences, leads and lists, sender email accounts and warmup, analytics, email verification, inbox placement, webhooks, workspaces, API keys, and reply management.

## Schema Source

Derived from the Instantly v2 REST API documentation at https://developer.instantly.ai/ and the published OpenAPI specification at https://api.instantly.ai/openapi/api_v2.json.

Authentication uses Bearer tokens (scoped API keys).

## Type Inventory

### Campaign Domain

- **Campaign** — top-level campaign resource with name, status, schedule, and sender assignments
- **CampaignDetails** — extended campaign representation including sequence steps, analytics summary, and tag associations
- **CampaignStatus** — enum of campaign lifecycle states (DRAFT, ACTIVE, PAUSED, COMPLETED, STOPPED)
- **CampaignType** — enum distinguishing outbound cold email from subsequence-triggered flows
- **CampaignSchedule** — sending window configuration with days of week, start/end times, and timezone
- **CampaignAnalytics** — aggregated metrics per campaign: sent, opened, clicked, replied, bounced, unsubscribed, interested

### Sequence Domain

- **Step** — abstract union type for sequence steps
- **SequenceStep** — ordered step within a campaign sequence with delay and variant list
- **EmailStep** — concrete step type carrying subject, body, and A/B variant details
- **WaitStep** — delay-only step defining a wait interval between email steps
- **Subsequence** — a branching sequence triggered by lead behavior (e.g., no reply after N days)
- **SubsequenceStep** — individual step within a subsequence

### Lead Domain

- **Lead** — core lead/contact record with email, first name, last name, company, and campaign assignment
- **LeadDetails** — extended lead with all custom variables, activity history, and interest status
- **LeadStatus** — enum of lead interest states (ACTIVE, INTERESTED, NOT_INTERESTED, MEETING_BOOKED, MEETING_COMPLETED, OUT_OF_OFFICE, WRONG_PERSON)
- **LeadList** — named list of leads that can be associated with campaigns
- **ListDetails** — extended list representation with lead count and creation metadata
- **LeadActivity** — timestamped event record for a single lead interaction (sent, opened, replied, etc.)
- **LeadStats** — aggregated per-lead engagement counts

### Email Domain

- **Email** — a sent or scheduled email message tied to a campaign step and lead
- **EmailDetails** — full email representation with headers, body, tracking metadata
- **EmailStatus** — enum of email delivery states (SCHEDULED, SENT, OPENED, CLICKED, REPLIED, BOUNCED, UNSUBSCRIBED)
- **Reply** — inbound reply message from a lead, surfaced in the unified inbox
- **ReplyDetails** — full reply with threading context and read/unread state
- **ReplyStatus** — enum marking a reply as UNREAD, READ, or ARCHIVED
- **Draft** — unsent draft reply composed by the user within the unified inbox

### Account Domain

- **Account** — alias for EmailAccount; the top-level sender mailbox resource
- **EmailAccount** — SMTP, Gmail, or Microsoft mailbox configured as a sender, with daily limit and status
- **AccountStatus** — enum of account health states (ACTIVE, PAUSED, ERROR, WARMING_UP)
- **AccountStats** — per-account sending volume and deliverability metrics

### Warmup Domain

- **Warmup** — warmup configuration attached to an email account
- **WarmupDetails** — extended warmup with ramp schedule, daily targets, and current progress
- **WarmupStatus** — enum of warmup states (ACTIVE, PAUSED, COMPLETED)
- **WarmupSchedule** — daily send/receive targets and increment rate for the warmup ramp

### Organization Domain

- **Tag** — label applied to campaigns or leads for filtering and segmentation
- **List** — collection of leads (alias surface for LeadList in query context)
- **Inbox** — unified reply inbox scoped to an account or workspace
- **InboxDetails** — extended inbox with unread count and filter state

### Deliverability Domain

- **Blacklist** — abstract blacklist record
- **GlobalBlacklist** — workspace-wide email address or domain suppression entry
- **CampaignBlacklist** — per-campaign suppression entry
- **Unsubscribe** — unsubscribe event record linked to a lead and campaign
- **EmailVerification** — single address verification result with syntax, MX, and risk fields
- **VerificationResult** — outcome enum (VALID, RISKY, INVALID, UNKNOWN)
- **BulkVerification** — batch verification job tracking status and result counts

### Analytics Domain

- **Analytics** — top-level analytics query result container
- **AnalyticsDetails** — time-series breakdown of campaign metrics over a date range

### Integration and Auth Domain

- **Variable** — custom merge variable defined at workspace or campaign level
- **Template** — reusable email template with subject and body placeholders
- **TemplateDetails** — extended template with usage stats and version history
- **Integration** — third-party integration record (Clay, HubSpot, Salesforce, Pipedrive, Zapier, Make, n8n, Slack)
- **APIKey** — scoped API key record with name, scopes, and creation date
- **Token** — short-lived session token used for OAuth-connected accounts

### Webhook Domain

- **Webhook** — webhook subscription with target URL and event filter list
- **WebhookEvent** — enum of subscribable event types (EMAIL_SENT, EMAIL_OPENED, EMAIL_REPLIED, EMAIL_BOUNCED, EMAIL_UNSUBSCRIBED, LEAD_INTERESTED, LEAD_STATUS_CHANGED)

### Workspace Domain

- **Workspace** — multi-tenant isolation boundary used by agencies and large teams
- **WorkspaceDetails** — extended workspace with member list, billing plan, and usage counters

### Inbox Placement Domain

- **InboxPlacementTest** — a deliverability test run across major mailbox providers
- **InboxPlacementResult** — per-provider result (inbox, spam, missing) for a placement test

## Query Surface

- `campaign(id)` / `campaigns(filters, pagination)` — fetch single or paginated campaigns
- `lead(id)` / `leads(campaignId, filters, pagination)` — fetch leads with filtering
- `emailAccount(id)` / `emailAccounts(filters)` — fetch sender mailbox accounts
- `analytics(campaignId, dateRange)` — fetch aggregated campaign analytics
- `inbox(accountId)` / `replies(filters)` — fetch unified inbox and reply threads
- `webhook(id)` / `webhooks()` — fetch webhook subscriptions
- `workspace(id)` / `workspaces()` — fetch workspace records
- `apiKeys()` — list scoped API keys
- `verifyEmail(address)` — trigger and return single address verification
- `bulkVerification(jobId)` — poll status of a bulk verification job
- `inboxPlacementTest(id)` / `inboxPlacementTests()` — fetch placement test results
- `tags()` / `lists()` / `templates()` — fetch organizational resources

## Mutation Surface

- `createCampaign` / `updateCampaign` / `deleteCampaign` / `launchCampaign` / `pauseCampaign`
- `createLead` / `updateLead` / `deleteLead` / `moveLead`
- `addEmailAccount` / `updateEmailAccount` / `removeEmailAccount`
- `startWarmup` / `pauseWarmup`
- `createWebhook` / `updateWebhook` / `deleteWebhook`
- `createAPIKey` / `revokeAPIKey`
- `addToBlacklist` / `removeFromBlacklist`
- `createTemplate` / `updateTemplate` / `deleteTemplate`
- `replyToLead` / `markReplyRead` / `archiveReply`
- `createInboxPlacementTest`
- `verifyEmailBulk`
