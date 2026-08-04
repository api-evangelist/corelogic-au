# CoreLogic Australia (corelogic-au)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

CoreLogic Australia — trading as Cotality since the 2025 global rebrand, and operating the RP Data platform through RP Data Pty Ltd — is the dominant independent property data, analytics and valuation provider in Australia and New Zealand. It sits in the middle of the Australian property value chain: it aggregates state land-registry and valuer-general records, agent and portal listing campaigns, auction results and rental campaigns into a single property spine, then sells that spine back to banks, mortgage brokers, valuers, insurers, agents and government. Its commercial products include the RP Data / RP Professional desktop, the IntelliVal automated valuation model, the CoreLogic Home Value Index, Cordell construction cost data, Cityscope commercial property data, and the PSX valuation ordering exchange. Its API posture is genuinely developer-facing but commercially licensed: a live Backstage-based Cotality Developer Portal at developer.corelogic.asia offers self-serve signup and self-serve creation of sandbox OAuth clients against a deliberately restricted evaluation dataset with request quotas, while every production API host in the *.api.cotality.com.au family answers 401 "Access token is missing" and requires a signed commercial data licence. Australia has no MLS and no RESO mandate — CoreLogic's RESO Web API and Data Dictionary certifications belong to Trestle, its United States MLS platform, not to this Australian surface. The Australian APIs are proprietary REST/JSON over an Apigee gateway with OAuth 2.0 client credentials; no OData $metadata, no RESO endpoint, and no RESO Universal Property Identifier appears anywhere in the Australian developer portal.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/corelogic-au/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/corelogic-au/refs/heads/main/apis.yml)

## Tags

- Real Estate
- Australia
- Property Data
- Valuation
- AVM
- PropTech
- Property Listings
- Rentals
- Auction Data
- Commercial Real Estate
- Mortgage
- Land Registry
- Cotality
- RP Data

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

### CoreLogic Australia Access API

OAuth 2.0 token service for every Cotality Australia and New Zealand API. Issues JWT access tokens via client_credentials, authorization_code and refresh_token grants. The developer portal documents POST https://access.api.cotality.com.au/as/token.oauth2 and POST https://access.api.cotality.com.au/oauth/token with HTTP Basic (base64 client_id:client_secret); the published sandbox collection shows the equivalent GET https://api.corelogic.asia/access/oauth/token?grant_type=client_credentials. Probed anonymously on 2026-07-26 and returned HTTP 401 unauthorized.

- **Human URL:** [https://developer.corelogic.asia/guides/api-authentication](https://developer.corelogic.asia/guides/api-authentication)
- **Base URL:** `https://access.api.cotality.com.au`

#### Tags

- Authentication
- OAuth 2.0
- JWT

#### Properties

- [Documentation](https://developer.corelogic.asia/guides/api-authentication)
- [Documentation](https://developer.corelogic.asia/guides/application-silent-login)
- [Postman Collection](collections/corelogic-au-rp-inside-auth-example.postman_collection.json)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Property Details API

Per-property record retrieval keyed on the CoreLogic property identifier — core and additional attributes, site detail, features, occupancy, sales history and last sale, on-the-market sales and rental campaigns, marketing contacts, and property photos. Thirteen operations are published in the CoreLogic APIs AU Sample Sandbox Collection under /au/properties/{propertyId}/*. Production host probed anonymously on 2026-07-26 and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/apis](https://developer.corelogic.asia/apis)
- **Base URL:** `https://property-details.api.cotality.com.au`

#### Tags

- Property Data
- Property Records
- Sales History
- Rentals

#### Properties

- [Documentation](https://developer.corelogic.asia/apis)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Property Services API

The older versioned property services family — comparables, geo sales search by polygon, locality, postcode and street, property and parcel suggest, point search, for-sale and for-rent advertisements, property pros-and-cons, marketing contacts, and property validation. Thirty-one operations are published in the sandbox collection under /au/v1/* and /au/v2/*. The collection references this family through unresolved Postman variables, so no production base URL is asserted here; the suggest and address-matcher hosts suggest.api.cotality.com.au and matcher.api.cotality.com.au both resolve and answered HTTP 401 on 2026-07-26.

- **Human URL:** [https://developer.corelogic.asia/apis](https://developer.corelogic.asia/apis)

#### Tags

- Property Search
- Comparables
- Geo Search
- Address Matching

#### Properties

- [Documentation](https://developer.corelogic.asia/apis)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Search API

Property search and address matching across Australia — radius search by latitude/longitude, and filtered search by council area, locality, postcode and street, each in four flavours (current attributes, last sale, on-the-market for rent, on-the-market for sale), plus the Address Matcher service that resolves a free-text address to a CoreLogic property identifier. Twenty-two operations are published in the sandbox collection. Production host probed anonymously on 2026-07-26 and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/address_matcher](https://developer.corelogic.asia/address_matcher)
- **Base URL:** `https://search.api.cotality.com.au`

#### Tags

- Property Search
- Address Matching
- Geo Search
- Property Listings

#### Properties

- [Documentation](https://developer.corelogic.asia/address_matcher)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia AVM API

IntelliVal automated valuation model — the valuation engine at the centre of CoreLogic Australia's mortgage and lending business. The sandbox collection publishes consumer and origination AVM variants, current and historical point-in-time valuations (/au/properties/{id}/avm/intellival/{variant}/{date}), a live AVM POST (/liveavm/intellival/consumer) and a banded live AVM (/liveavm/intellival/consumer/band), with a roundTo parameter. Production host probed anonymously on 2026-07-26 and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/apis](https://developer.corelogic.asia/apis)
- **Base URL:** `https://avm.api.cotality.com.au`

#### Tags

- AVM
- Valuation
- Mortgage
- IntelliVal

#### Properties

- [Documentation](https://developer.corelogic.asia/apis)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Auction API

Australian auction results and clearance rates — the weekly number the Australian property press runs on. Publishes state-level summaries and results with capital-city filtering, suburb and postcode detail, clearance-rate statistics, multi-week windows, date-range search and year-on-year comparison. Thirteen operations are published in the sandbox collection. Production host probed anonymously on 2026-07-26 and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/apis](https://developer.corelogic.asia/apis)
- **Base URL:** `https://auction.api.cotality.com.au`

#### Tags

- Auction Data
- Clearance Rate
- Market Data

#### Properties

- [Documentation](https://developer.corelogic.asia/apis)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Statistics API

Suburb, locality and region statistics plus ABS census summaries, driven by location and location-type identifiers and metric-type identifiers. Four operations are published in the sandbox collection, including POST /v1/statistics.json and the census summary service. Production host probed anonymously on 2026-07-26 and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/metrics](https://developer.corelogic.asia/metrics)
- **Base URL:** `https://statistics.api.cotality.com.au`

#### Tags

- Market Data
- Statistics
- Census

#### Properties

- [Documentation](https://developer.corelogic.asia/metrics)
- [Documentation](https://developer.corelogic.asia/metrics/census)
- [Documentation](https://developer.corelogic.asia/metrics/marketTrends)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Charts API

Server-rendered PNG chart images for market trends and census data, driven by location, property-type and metric-type identifiers with extensive presentation parameters (chart size, colours, titles, axis labels, marker radius, grid line style, date range, multi-series). Four operations are published in the sandbox collection. Production host probed anonymously on 2026-07-26 and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/explore_charts_customisation](https://developer.corelogic.asia/explore_charts_customisation)
- **Base URL:** `https://charts.api.cotality.com.au`

#### Tags

- Charts
- Market Data
- Data Visualization

#### Properties

- [Documentation](https://developer.corelogic.asia/explore_charts_customisation)
- [Documentation](https://developer.corelogic.asia/guides/charts-customisation)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Property Timeline API

Chronological event timeline for a single property — sales, listing campaigns, rental campaigns and, with the withBuildingConsents flag, building consent events. Three operations are published in the sandbox collection under /au/properties/{id}/timeline. Production host probed anonymously on 2026-07-26 and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/apis](https://developer.corelogic.asia/apis)
- **Base URL:** `https://property-timeline.api.cotality.com.au`

#### Tags

- Property Data
- Timeline
- Building Consents

#### Properties

- [Documentation](https://developer.corelogic.asia/apis)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia Content API

Serves the legal disclaimers that licensees are contractually required to display alongside CoreLogic data, retrieved by disclaimer key (for example /legal/disclaimers/auction_au and /legal/disclaimers/auction_standalone_au). It is also the host of the only anonymously readable machine-readable artifact CoreLogic Australia publishes: the RP.Inside authentication Postman collection at https://api.corelogic.asia/content/docs/public/deep-link-postman.json, fetched HTTP 200 on 2026-07-26. The production host probed anonymously on the same date and returned HTTP 401 "Access token is missing".

- **Human URL:** [https://developer.corelogic.asia/apis](https://developer.corelogic.asia/apis)
- **Base URL:** `https://content.api.cotality.com.au`

#### Tags

- Content
- Legal
- Disclaimers

#### Properties

- [Documentation](https://developer.corelogic.asia/apis)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)

### CoreLogic Australia PSX API

PSX is CoreLogic Australia's valuation ordering exchange, connecting lenders and brokers to panels of licensed valuers. The Cotality Developer Portal defines nine documented PSX operations — panel lookup, subscribe, pull notifications, expanded search, get order, update order, cancel, attach or retrieve documents, and set retrieved — plus a PSX implementation guide with quote, pre-ordering, ordering and valuation workflow diagrams. No base URL is published outside the authenticated portal, and no sample collection for PSX is public, so none is asserted here.

- **Human URL:** [https://developer.corelogic.asia/apis/psx-apis/psx-get-order](https://developer.corelogic.asia/apis/psx-apis/psx-get-order)

#### Tags

- Valuation
- Valuation Ordering
- Mortgage
- Workflow

#### Properties

- [Documentation](https://developer.corelogic.asia/guides/psx-implementation)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-panel-lookup)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-subscribe)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-pull-notifications)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-expanded-search)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-get-order)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-update-order)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-cancel)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-attach-or-retrieve-documents)
- [Documentation](https://developer.corelogic.asia/apis/psx-apis/psx-set-retrieved)

## Common Properties

- [Website](https://www.cotality.com/au)
- [Developer Portal](https://developer.corelogic.asia/)
- [Documentation](https://developer.corelogic.asia/apis)
- [Getting Started](https://developer.corelogic.asia/guides/quick-start)
- [Sign Up](https://developer.corelogic.asia/signup)
- [Login](https://developer.corelogic.asia/user/register)
- [Authentication](https://developer.corelogic.asia/guides/api-authentication)
- [Well-Known](https://auth.corelogic.asia/.well-known/openid-configuration)
- [Conventions](https://developer.corelogic.asia/guides/standards-and-conventions)
- [Sandbox](https://developer.corelogic.asia/guides/sandbox-test-data)
- [Support](https://developer.corelogic.asia/contact-us)
- [FAQ](https://developer.corelogic.asia/faq)
- [Terms of Service](https://developer.corelogic.asia/terms-and-conditions)
- [Privacy Policy](https://developer.corelogic.asia/legal/privacy-policy)
- [Postman Collection](collections/corelogic-au-sample-sandbox.postman_collection.json)
- [Postman Collection](collections/corelogic-au-rp-inside-auth-example.postman_collection.json)
- [LinkedIn](https://www.linkedin.com/company/cotality)

## Maintainers

- **Kin Lane** — kin@apievangelist.com
