# Instantly (instantly-ai)

Instantly is a cold email outbound platform that combines mailbox sending infrastructure, email warmup, a B2B lead database, deliverability tools, and a unified inbox for replies. The Instantly v2 REST API at api.instantly.ai/api/v2 covers campaigns, leads, accounts, email verification, inbox placement tests, webhooks, analytics, API keys, and workspaces, with Bearer token authentication and scoped API keys.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/instantly-ai/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/instantly-ai/refs/heads/main/apis.yml)

## Tags

- Cold Email
- Outbound
- Sales
- Deliverability
- Lead Database
- Email Verification
- Webhooks

## Timestamps

- **Created:** 2026-05-23
- **Modified:** 2026-05-23

## APIs

### Instantly Campaigns API

REST endpoints to create, list, fetch, update, launch, pause, and schedule cold email campaigns, plus manage sequences, A/B variants, and sender mailbox assignments.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/campaign](https://developer.instantly.ai/api-reference/groups/campaign)
- **Base URL:** `https://api.instantly.ai/api/v2/campaigns`

#### Tags

- Campaigns
- Sequences

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/campaign)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly Leads API

Endpoints to create, list, fetch, update, and delete leads, manage lead lists, move leads between campaigns, and update lead interest status.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/lead](https://developer.instantly.ai/api-reference/groups/lead)
- **Base URL:** `https://api.instantly.ai/api/v2/leads`

#### Tags

- Leads
- Contacts
- Lists

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/lead)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly Accounts API

Endpoints to add, list, update, and remove sender email accounts (SMTP, Gmail, Microsoft), configure per-account sending limits, and toggle warmup state.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/account](https://developer.instantly.ai/api-reference/groups/account)
- **Base URL:** `https://api.instantly.ai/api/v2/accounts`

#### Tags

- Email Accounts
- Mailboxes
- Warmup

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/account)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly Email Verification API

Single and bulk email address verification endpoints that check syntax, MX records, deliverability, and risk scoring before sending.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/email-verification](https://developer.instantly.ai/api-reference/groups/email-verification)
- **Base URL:** `https://api.instantly.ai/api/v2/email-verification`

#### Tags

- Verification
- Deliverability
- Email

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/email-verification)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly Inbox Placement Test API

Endpoints to run and read inbox placement tests across major mailbox providers, used to measure deliverability and quantify spam-folder risk before launching campaigns.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/inbox-placement-test](https://developer.instantly.ai/api-reference/groups/inbox-placement-test)
- **Base URL:** `https://api.instantly.ai/api/v2/inbox-placement-tests`

#### Tags

- Inbox Placement
- Deliverability
- Testing

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/inbox-placement-test)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly Webhooks API

CRUD endpoints for webhook subscriptions on campaign, lead, and account events (sent, opened, replied, bounced, unsubscribed) for streaming activity to external systems.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/webhook](https://developer.instantly.ai/api-reference/groups/webhook)
- **Base URL:** `https://api.instantly.ai/api/v2/webhooks`

#### Tags

- Webhooks
- Events
- Subscriptions

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/webhook)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly Analytics API

Campaign and account-level analytics — sent, open, click, reply, bounce, unsubscribe, and interested-lead counts aggregated over time ranges.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/analytics](https://developer.instantly.ai/api-reference/groups/analytics)
- **Base URL:** `https://api.instantly.ai/api/v2`

#### Tags

- Analytics
- Reporting
- Metrics

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/analytics)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly API Keys API

Endpoints to create, list, scope, and revoke API keys — the v2 API uses scoped Bearer tokens that can be restricted to specific resource permissions.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/api-key](https://developer.instantly.ai/api-reference/groups/api-key)
- **Base URL:** `https://api.instantly.ai/api/v2/api-keys`

#### Tags

- API Keys
- Auth
- Scopes

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/api-key)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Instantly Workspaces API

Endpoints for managing workspaces — the multi-tenant boundary used by agencies and large teams to isolate campaigns, accounts, and billing.

- **Human URL:** [https://developer.instantly.ai/api-reference/groups/workspace](https://developer.instantly.ai/api-reference/groups/workspace)
- **Base URL:** `https://api.instantly.ai/api/v2/workspaces`

#### Tags

- Workspaces
- Multi-Tenant
- Agency

#### Properties

- [Documentation](https://developer.instantly.ai/api-reference/groups/workspace)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/instantly-ai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/instantly-ai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://instantly.ai)
- [App](https://app.instantly.ai)
- [Documentation](https://developer.instantly.ai)
- [API Reference](https://developer.instantly.ai/api-reference)
- [Getting Started](https://developer.instantly.ai/getting-started/getting-started)
- [Authentication](https://developer.instantly.ai/getting-started/authorization)
- [OpenAPI](https://api.instantly.ai/openapi/api_v2.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Pricing](https://instantly.ai/pricing)
- [Blog](https://instantly.ai/blog)
- [Help](https://help.instantly.ai)
- [Sign Up](https://app.instantly.ai/auth/signup)
- [Sign In](https://app.instantly.ai/auth/login)
- [Privacy Policy](https://instantly.ai/privacy-policy)
- [Terms of Service](https://instantly.ai/terms)
- [LinkedIn](https://www.linkedin.com/company/instantlyai)
- [Twitter](https://x.com/Instantlydotai)
- [YouTube](https://www.youtube.com/@instantly-ai)
- [L L Ms Txt](https://developer.instantly.ai/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
