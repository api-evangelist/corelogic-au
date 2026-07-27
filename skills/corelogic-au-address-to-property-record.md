---
name: Resolve an Australian address to a CoreLogic property record
description: >-
  Turn free text like "2 Albert Avenue Broadbeach QLD 4218" into a CoreLogic property identifier,
  then pull the full property record — attributes, site, features, occupancy, sale history, images
  and current campaigns.
api: CoreLogic Australia Search API + Property Details API
grounding: collections/corelogic-au-sample-sandbox.postman_collection.json
generated: '2026-07-26'
method: generated
operations:
  - GET /au/matcher/address
  - GET /au/v2/suggest.json
  - GET /au/properties/{propertyId}/attributes/core
  - GET /au/properties/{propertyId}/attributes/additional
  - GET /au/properties/{propertyId}/site
  - GET /au/properties/{propertyId}/features
  - GET /au/properties/{propertyId}/occupancy
  - GET /au/properties/{propertyId}/sales
  - GET /au/properties/{propertyId}/sales/last
  - GET /au/properties/{propertyId}/otm/campaign/sales
  - GET /au/properties/{propertyId}/otm/campaign/rent
  - GET /au/properties/{propertyId}/images/
  - GET /au/properties/{propertyId}/images/default
  - GET /au/properties/{propertyId}/contacts
---

# Resolve an address to a CoreLogic property record

Australia has no MLS and no RESO UPI. The join key across the whole Cotality estate is an **opaque
numeric CoreLogic property identifier**, and almost every workflow starts by resolving one.

Hold a bearer token first — see `corelogic-au-authenticate-and-call.md`.

## Step 1 — resolve the identifier

**Preferred: Address Matcher** (Search Services, `search.api.cotality.com.au`):

```
GET /au/matcher/address?clientName=<yourAppName>&q=2 Albert Avenue Broadbeach QLD 4218&matchProfileId=1
```

The response carries match types and codes describing how confident the match is; interpret them
before you accept the identifier.

**Alternative: Suggest** (Property Services, `property-au.api.cotality.com.au` — this family is
marked **deprecated** in Cotality's environment table, so prefer Address Matcher for new work):

```
GET /au/v2/suggest.json?q=2 Albert&suggestionTypes=address,street,locality,postcode&limit=10&includeUnits=true&returnSuggestion=byType
```

Suggest uses **starts-with** matching with no fuzzy fallback. A wrong prefix returns
`402: No data found for your search.` — that is a no-match, not a billing error.

## Step 2 — pull the record

With `propertyId` in hand, call Property Details (`property-details.api.cotality.com.au`). Each
facet is its own resource, so request only what you need:

```
GET /au/properties/{propertyId}/attributes/core         # beds, baths, car spaces, land area, type
GET /au/properties/{propertyId}/attributes/additional   # extended attributes
GET /au/properties/{propertyId}/site                    # site / parcel detail
GET /au/properties/{propertyId}/features                # feature flags
GET /au/properties/{propertyId}/occupancy               # owner-occupied / rented / vacant
GET /au/properties/{propertyId}/sales                   # full sale history
GET /au/properties/{propertyId}/sales/last              # most recent sale only
GET /au/properties/{propertyId}/otm/campaign/sales      # current for-sale campaign
GET /au/properties/{propertyId}/otm/campaign/rent       # current rental campaign
GET /au/properties/{propertyId}/images/                 # photo list
GET /au/properties/{propertyId}/images/default          # hero photo
GET /au/properties/{propertyId}/contacts                # marketing contacts
```

## Step 3 — get the timeline instead, when you want chronology

```
GET https://property-timeline.api.cotality.com.au/au/properties/{propertyId}/timeline
GET https://property-timeline.api.cotality.com.au/au/properties/{propertyId}/timeline?withBuildingConsents
```

## Rules that will bite you

- **Do not persist property identifiers as permanent keys.** Cotality documents that a saved id
  can stop resolving because the property was *deduplicated*, *made obsolete*, or *split or
  merged*. Re-resolve from the address on a schedule.
- **Images are pass-through.** Supplier files arrive as WebP, JPG, JPEG, PNG, TIFF, GIF or RAW and
  the published list is explicitly not exhaustive. Support WebP or your PDF/render pipeline will
  break.
- **Display the disclaimers.** Licensees are contractually required to show Cotality legal notices
  alongside the data; fetch them from the Content API at
  `https://content.api.cotality.com.au/legal/disclaimers/{key}`. Legal content is **not** available
  in the sandbox — it appears once you are promoted to UAT.
- **Sandbox coverage is 29 suburbs.** If you are testing, use a property from
  `sandbox/corelogic-au-sandbox.yml` — for example `47872329` (2 Albert Avenue, Broadbeach QLD
  4218). Any other real address will legitimately return no data.
