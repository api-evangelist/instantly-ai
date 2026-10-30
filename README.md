# Instantly

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Instantly is a cold email outbound platform that combines mailbox sending infrastructure, email warmup, a B2B lead database, deliverability tools, and a unified inbox for replies. The Instantly v2 REST API at api.instantly.ai/api/v2 publishes a 173-operation OpenAPI 3.1 covering campaigns and subsequences, leads and lead lists, sending accounts and warmup, email verification, inbox placement tests, SuperSearch enrichment, blocklists, custom tags, audit logs, background jobs, webhooks, analytics, API keys, workspaces and workspace groups. Authentication is a scoped Bearer API key backed by a full OAuth 2.0 authorization server with 178 published scopes, PKCE and dynamic client registration. Instantly also runs a hosted remote MCP server, publishes an A2A agent card, an llms.txt and first-party Agent Skills.

**Areas:** Cold Email · Outbound · Sales · Deliverability · Lead Database · Email Verification · Webhook · A2A

## Instantly on APIs.io

Everything profiled for Instantly is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/instantly-ai/](https://apis.io/providers/instantly-ai/)** — or go straight to one of the APIs or properties below.

### APIs (29)

- [Instantly Account API](https://apis.io/apis/instantly-ai/instantly-ai-account-api/) — An email account that can be used to send campaigns
- [Instantly Account Campaign Mapping API](https://apis.io/apis/instantly-ai/instantly-ai-accountcampaignmapping-api/) — Account Campaign Mapping
- [Instantly Analytics API](https://apis.io/apis/instantly-ai/instantly-ai-analytics-api/) — Endpoints related to analytics
- [Instantly Block List Entry API](https://apis.io/apis/instantly-ai/instantly-ai-blocklistentry-api/) — A blocked email or domain
- [Instantly Campaign API](https://apis.io/apis/instantly-ai/instantly-ai-campaign-api/) — A campaign that can be sent to a list of recipients
- [Instantly Campaign Subsequence API](https://apis.io/apis/instantly-ai/instantly-ai-campaignsubsequence-api/) — A subsequence entity representing a follow-up sequence
- [Instantly CRM Actions API](https://apis.io/apis/instantly-ai/instantly-ai-crmactions-api/) — CRM related actions
- [Instantly Custom Tag API](https://apis.io/apis/instantly-ai/instantly-ai-customtag-api/) — A custom tag for organizing and categorizing accounts and campaigns. You can use them as filters in apis that list accounts and campaigns.
- [Instantly Custom Tag Mapping API](https://apis.io/apis/instantly-ai/instantly-ai-customtagmapping-api/) — This entity represents a tag being assigned to a specific campaign or email account. When an email account is assigned a tag, a new custom tag mapping entry…
- [Instantly DFY Email Account Order API](https://apis.io/apis/instantly-ai/instantly-ai-dfyemailaccountorder-api/) — A Done-For-You email account order
- [Instantly Email API](https://apis.io/apis/instantly-ai/instantly-ai-email-api/) — A campaign email, a reply, a manually sent email, or any other email that's visible in the Unibox
- [Instantly Inbox Placement Analytics API](https://apis.io/apis/instantly-ai/instantly-ai-inboxplacementanalytics-api/) — Analytics data for individual emails in inbox placement tests
- [Instantly Inbox Placement Blacklist And Spam Assassin Report API](https://apis.io/apis/instantly-ai/instantly-ai-inboxplacementblacklistandspamassassinreport-api/) — Report data for an inbox placement test
- [Instantly Inbox Placement Test API](https://apis.io/apis/instantly-ai/instantly-ai-inboxplacementtest-api/) — An inbox placement test
- [Instantly Lead API](https://apis.io/apis/instantly-ai/instantly-ai-lead-api/) — A lead entity representing an individual lead
- [Instantly Lead Label API](https://apis.io/apis/instantly-ai/instantly-ai-leadlabel-api/) — A custom label for categorizing and managing leads
- [Instantly Lead List API](https://apis.io/apis/instantly-ai/instantly-ai-leadlist-api/) — A list used to store leads
- [Instantly Super Search Enrichment API](https://apis.io/apis/instantly-ai/instantly-ai-supersearchenrichment-api/) — An enrichment can take different forms, such as email enrichment or LinkedIn enrichment. Leads may be imported from SuperSearch using the dedicated…
- [Instantly Webhook API](https://apis.io/apis/instantly-ai/instantly-ai-webhook-api/) — A webhook subscription for receiving event notifications
- [Instantly Workspace API](https://apis.io/apis/instantly-ai/instantly-ai-workspace-api/) — A workspace entity representing a workspace
- [Instantly Workspace Billing API](https://apis.io/apis/instantly-ai/instantly-ai-workspacebilling-api/) — Workspace Billing
- [Instantly Workspace Group Member API](https://apis.io/apis/instantly-ai/instantly-ai-workspacegroupmember-api/) — A member of a workspace group. You can use the endpoints within this entity to manage the members of a workspace group.
- [Instantly Workspace Member API](https://apis.io/apis/instantly-ai/instantly-ai-workspacemember-api/) — A member of a workspace with associated user details
- [Instantly O Auth API](https://apis.io/apis/instantly-ai/instantly-ai-oauth-api/) — OAuth authentication endpoints for connecting Google and Microsoft email accounts
- [Instantly API Key API](https://apis.io/apis/instantly-ai/instantly-ai-api-key-api/) — API Key
- [Instantly Audit Log API](https://apis.io/apis/instantly-ai/instantly-ai-audit-log-api/) — Audit log records for tracking system activities
- [Instantly Background Job API](https://apis.io/apis/instantly-ai/instantly-ai-background-job-api/) — A background job that can be used to perform long-running tasks
- [Instantly Email Verification API](https://apis.io/apis/instantly-ai/instantly-ai-email-verification-api/) — A single email verification
- [Instantly Webhook Event API](https://apis.io/apis/instantly-ai/instantly-ai-webhook-event-api/) — A webhook event that was sent or attempted to be sent

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Instantly Ai Webhooks](https://apis.io/asyncapis/instantly-ai/instantly-ai-webhooks/)

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/instantly-ai/](https://apis.io/graphqls/instantly-ai/instantly-ai-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [instantly-ai-mcp.yml](https://apis.io/servers/instantly-ai/instantly-ai-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Instantly Ai Agentic Access](https://apis.io/agentic-access/instantly-ai/instantly-ai-agentic-access/)

#### Collections (2)

Postman and Open Collection request collections.

- [Instantly.ai API v2](https://apis.io/collections/instantly-ai/open-instantly-ai/)
- [Instantly.ai API v2 Campaigns API](https://apis.io/collections/instantly-ai/open-instantly-ai-campaigns-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Instantly Ai Api V2 Overlay](https://apis.io/overlays/instantly-ai/instantly-ai-api-v2-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Instantly Ai Authentication](https://apis.io/security/instantly-ai/instantly-ai-authentication/)
- [Instantly Ai Domain Security](https://apis.io/security/instantly-ai/instantly-ai-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Instantly Ai Scopes](https://apis.io/scopes/instantly-ai/instantly-ai-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Instantly Ai Plans Pricing](https://apis.io/plans/instantly-ai/instantly-ai-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Instantly Ai Rate Limits](https://apis.io/rate-limits/instantly-ai/instantly-ai-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Instantly Ai Finops](https://apis.io/finops/instantly-ai/instantly-ai-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://instantly.ai)
- [Documentation](https://developer.instantly.ai)
- [Getting started](https://developer.instantly.ai/getting-started/getting-started)
- [API reference](https://developer.instantly.ai/api-reference)
- [Pricing](https://instantly.ai/pricing)
- [Sign up](https://app.instantly.ai/auth/signup)
- [Support](https://help.instantly.ai)
- [Blog](https://instantly.ai/blog)
- [Terms of service](https://instantly.ai/terms)
- [Privacy policy](https://instantly.ai/privacy-policy)
- [GitHub](https://github.com/Instantly-ai)

## API Evangelist rating

**Kin Score 64.0** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 60.8 |
| Contract governance | 4.5 |
| Operational transparency | 50.0 |
| Developer ergonomics | 78.6 |
| Access clarity | 76.3 |

**Agent readiness 60.5** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 34.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/instantly-ai/](https://apis.io/providers/instantly-ai/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Instantly: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/instantly-ai/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
