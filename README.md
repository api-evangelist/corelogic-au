# CoreLogic Australia

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

CoreLogic Australia — trading as Cotality since the 2025 global rebrand, and operating the RP Data platform through RP Data Pty Ltd — is the dominant independent property data, analytics and valuation provider in Australia and New Zealand. It sits in the middle of the Australian property value chain: it aggregates state land-registry and valuer-general records, agent and portal listing campaigns, auction results and rental campaigns into a single property spine, then sells that spine back to banks, mortgage brokers, valuers, insurers, agents and government. Its commercial products include the RP Data / RP Professional desktop, the IntelliVal automated valuation model, the CoreLogic Home Value Index, Cordell construction cost data, Cityscope commercial property data, and the PSX valuation ordering exchange. Its API posture is genuinely developer-facing but commercially licensed: a live Backstage-based Cotality Developer Portal at developer.corelogic.asia offers self-serve signup and self-serve creation of sandbox OAuth clients against a deliberately restricted evaluation dataset with request quotas, while every production API host in the *.api.cotality.com.au family answers 401 "Access token is missing" and requires a signed commercial data licence. Australia has no MLS and no RESO mandate — CoreLogic's RESO Web API and Data Dictionary certifications belong to Trestle, its United States MLS platform, not to this Australian surface. The Australian APIs are proprietary REST/JSON over an Apigee gateway with OAuth 2.0 client credentials; no OData $metadata, no RESO endpoint, and no RESO Universal Property Identifier appears anywhere in the Australian developer portal.

**Areas:** Real Estate · Australia · Property Data · Valuation · AVM · PropTech · Property Listings · Rentals · Auction Data · Commercial Real Estate · Mortgage · Land Registry

## CoreLogic Australia on APIs.io

Everything profiled for CoreLogic Australia is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/corelogic-au/](https://apis.io/providers/corelogic-au/)** — or go straight to one of the APIs or properties below.

### APIs (26)

- [CoreLogic Australia Access API](https://apis.io/apis/corelogic-au/corelogic-au-access-api/) — OAuth 2.0 token service for every Cotality Australia and New Zealand API. Issues JWT access tokens via client_credentials, authorization_code and…
- [CoreLogic Australia Property Details API](https://apis.io/apis/corelogic-au/corelogic-au-property-details-api/) — Per-property record retrieval keyed on the CoreLogic property identifier — core and additional attributes, site detail, features, occupancy, sales history…
- [CoreLogic Australia Property Services API](https://apis.io/apis/corelogic-au/corelogic-au-property-services-api/) — The older versioned property services family — comparables, geo sales search by polygon, locality, postcode and street, property and parcel suggest, point…
- [CoreLogic Australia Search API](https://apis.io/apis/corelogic-au/corelogic-au-search-api/) — Property search and address matching across Australia — radius search by latitude/longitude, and filtered search by council area, locality, postcode and…
- [CoreLogic Australia AVM API](https://apis.io/apis/corelogic-au/corelogic-au-avm-api/) — IntelliVal automated valuation model — the valuation engine at the centre of CoreLogic Australia's mortgage and lending business. The sandbox collection…
- [CoreLogic Australia Auction API](https://apis.io/apis/corelogic-au/corelogic-au-auction-api/) — Australian auction results and clearance rates — the weekly number the Australian property press runs on. Publishes state-level summaries and results with…
- [CoreLogic Australia Statistics API](https://apis.io/apis/corelogic-au/corelogic-au-statistics-api/) — Suburb, locality and region statistics plus ABS census summaries, driven by location and location-type identifiers and metric-type identifiers. Four…
- [CoreLogic Australia Charts API](https://apis.io/apis/corelogic-au/corelogic-au-charts-api/) — Server-rendered PNG chart images for market trends and census data, driven by location, property-type and metric-type identifiers with extensive…
- [CoreLogic Australia Property Timeline API](https://apis.io/apis/corelogic-au/corelogic-au-property-timeline-api/) — Chronological event timeline for a single property — sales, listing campaigns, rental campaigns and, with the withBuildingConsents flag, building consent…
- [CoreLogic Australia Content API](https://apis.io/apis/corelogic-au/corelogic-au-content-api/) — Serves the legal disclaimers that licensees are contractually required to display alongside CoreLogic data, retrieved by disclaimer key (for example…
- [CoreLogic Australia PSX API](https://apis.io/apis/corelogic-au/corelogic-au-psx-api/) — PSX is CoreLogic Australia's valuation ordering exchange, connecting lenders and brokers to panels of licensed valuers. The Cotality Developer Portal…
- [CoreLogic Australia Commercial API](https://apis.io/apis/corelogic-au/corelogic-au-commercial-api/) — Commercial property data delivered into a licensee's own systems — market research, commercial valuations and comparable sales analysis, sharing the…
- [CoreLogic Australia Construction API](https://apis.io/apis/corelogic-au/corelogic-au-construction-api/) — Live Cordell construction cost and project intelligence — project activity, builder profiles and contact information — delivered into customer-facing…
- [CoreLogic Australia Insurance API](https://apis.io/apis/corelogic-au/corelogic-au-insurance-api/) — Insurance-facing property data service. Named and hosted in the Cotality Developer Portal environment-details guide, and included in the sandbox at…
- [CoreLogic Australia Property Risk API](https://apis.io/apis/corelogic-au/corelogic-au-property-risk-api/) — Property risk services — the API behind Cotality's Australian hazard and resilience products. Named and hosted in the environment-details guide (sandbox…
- [CoreLogic Australia Places API](https://apis.io/apis/corelogic-au/corelogic-au-places-api/) — Places of interest attached to a property. The portal FAQ is explicit about its scope — "Currently, only Schools and School Catchments are available" — and…
- [CoreLogic Australia Location Search API](https://apis.io/apis/corelogic-au/corelogic-au-location-search-api/) — Location search services — the successor surface for resolving the locality, postcode, street, council-area and state identifiers every Cotality search,…
- [CoreLogic Australia Property Bureau API](https://apis.io/apis/corelogic-au/corelogic-au-property-bureau-api/) — Property Bureau service. Named and hosted in the Cotality Developer Portal environment-details guide and included in the sandbox at…
- [CoreLogic Australia AVM Report API](https://apis.io/apis/corelogic-au/corelogic-au-avm-report-api/) — Report rendering for IntelliVal automated valuations — the document form of the AVM number rather than the raw estimate. Named and hosted in the…
- [CoreLogic Australia Property Profile Report API](https://apis.io/apis/corelogic-au/corelogic-au-property-profile-report-api/) — Property profile report generation — the API behind Cotality's Australian property, suburb and investment report products. Named and hosted in the…
- [CoreLogic Australia Reporting API](https://apis.io/apis/corelogic-au/corelogic-au-reporting-api/) — Reporting services. Named and hosted in the Cotality Developer Portal environment-details guide and included in the sandbox at…
- [CoreLogic Australia Property Monitor API](https://apis.io/apis/corelogic-au/corelogic-au-property-monitor-api/) — Property monitoring — watch a property or portfolio for change. Named and hosted in the environment-details guide, and explicitly excluded from the sandbox…
- [CoreLogic Australia Notification API](https://apis.io/apis/corelogic-au/corelogic-au-notification-api/) — Notification services. Named and hosted in the environment-details guide and excluded from the sandbox alongside Property Monitor; probed anonymously on…
- [CoreLogic Australia Owner Verification API](https://apis.io/apis/corelogic-au/corelogic-au-owner-verification-api/) — Property owner verification services. Named and hosted in the environment-details guide and excluded from the sandbox ("Property Owner Verification"), so it…
- [CoreLogic Australia Update API](https://apis.io/apis/corelogic-au/corelogic-au-update-api/) — Update services — the write-shaped surface of the Cotality Australian estate. Named and hosted in the environment-details guide and excluded from the…
- [CoreLogic Australia Cordell Sum Sure API](https://apis.io/apis/corelogic-au/corelogic-au-cordell-sum-sure-api/) — Cordell Sum Sure — building and contents rebuild-cost estimation, the calculator Australian insurers and brokers use for sum-insured adequacy. Named and…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Corelogic Au Psx Webhooks](https://apis.io/asyncapis/corelogic-au/corelogic-au-psx-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Cotality MCP Server](https://apis.io/servers/corelogic-au/cotality-mcp-server/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Corelogic Au Authentication](https://apis.io/security/corelogic-au/corelogic-au-authentication/)
- [Corelogic Au Domain Security](https://apis.io/security/corelogic-au/corelogic-au-domain-security/)
- [Corelogic Au Vulnerability Disclosure](https://apis.io/security/corelogic-au/corelogic-au-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Corelogic Au Scopes](https://apis.io/scopes/corelogic-au/corelogic-au-scopes/)

#### Rate limits (1)

Published request limits.

- [Corelogic Au Rate Limits](https://apis.io/rate-limits/corelogic-au/corelogic-au-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.cotality.com/au)
- [Documentation](https://developer.corelogic.asia/apis)
- [Getting started](https://developer.corelogic.asia/guides/quick-start)
- [API reference](https://developer.corelogic.asia/apis)
- [Sign up](https://developer.corelogic.asia/signup)
- [Support](https://developer.corelogic.asia/contact-us)
- [Blog](https://www.cotality.com/au/insights)
- [Security](https://www.cotality.com/security)
- [Terms of service](https://developer.corelogic.asia/terms-and-conditions)
- [Privacy policy](https://developer.corelogic.asia/legal/privacy-policy)

## API Evangelist rating

**Kin Score 29.3** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 39.0 |
| Contract governance | 18.2 |
| Operational transparency | 18.4 |
| Developer ergonomics | 18.5 |
| Access clarity | 6.6 |

**Agent readiness 26.1** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 32.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/corelogic-au/](https://apis.io/providers/corelogic-au/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for CoreLogic Australia: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/corelogic-au/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
