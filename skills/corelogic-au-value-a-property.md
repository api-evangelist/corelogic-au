---
name: Value an Australian property with IntelliVal and back it with comparables
description: >-
  Get a current or historical IntelliVal automated valuation for a property, choose correctly
  between the consumer and origination variants and between static and live AVMs, and support the
  number with rule-driven comparable sales.
api: CoreLogic Australia AVM API + Property Services API
grounding: collections/corelogic-au-sample-sandbox.postman_collection.json
generated: '2026-07-26'
method: generated
operations:
  - GET /au/properties/{propertyId}/avm/intellival/consumer/current
  - GET /au/properties/{propertyId}/avm/intellival/consumer/{valuationDate}
  - GET /au/properties/{propertyId}/avm/intellival/origination
  - GET /au/properties/{propertyId}/avm/intellival/origination/current
  - GET /au/properties/{propertyId}/avm/intellival/origination/{valuationDate}
  - POST /au/properties/{propertyId}/liveavm/intellival/consumer
  - POST /au/properties/{propertyId}/liveavm/intellival/consumer/band
  - POST /au/v1/property/comparables.json
---

# Value a property with IntelliVal

IntelliVal is Cotality's Australian automated valuation model — the number that sits under a large
share of Australian mortgage and lending workflow. Base host:
`https://avm.api.cotality.com.au` (sandbox: `https://api-sbox.corelogic.asia/avm`).

Hold a bearer token first — see `corelogic-au-authenticate-and-call.md`. Resolve the
`propertyId` first — see `corelogic-au-address-to-property-record.md`.

## Choose the variant deliberately

- **consumer** — the consumer-facing estimate.
- **origination** — the lending/origination estimate. This variant is **excluded from the sandbox**
  ("AVM - origination type" is on Cotality's published list of collections the sandbox does not
  include); you need UAT or production access to exercise it.

## Static valuations (GET)

```
GET /au/properties/{propertyId}/avm/intellival/consumer/current
GET /au/properties/{propertyId}/avm/intellival/consumer/2022-07-01
GET /au/properties/{propertyId}/avm/intellival/origination/current?roundTo=1000
GET /au/properties/{propertyId}/avm/intellival/origination
GET /au/properties/{propertyId}/avm/intellival/origination/2021-01-01?roundTo=1000
```

The date segment is an ISO `YYYY-MM-DD` point in time; omitting the trailing segment on
`origination` returns the valuation history. `roundTo` controls rounding of the returned value
(Cotality's own samples use `roundTo=1000`).

## Live valuations (POST)

Live AVMs recompute rather than serve a stored figure, and take a JSON request body:

```
POST /au/properties/{propertyId}/liveavm/intellival/consumer
POST /au/properties/{propertyId}/liveavm/intellival/consumer/band
```

Use the `/band` form when you need a value **range** rather than a point estimate — the right
choice for consumer-facing display where a false-precision single number is a liability.

## Back the number with comparables

Comparables live on the older Property Services family
(`https://property-au.api.cotality.com.au`, marked **deprecated** — plan a migration, but it is
what publishes comparables today):

```
POST /au/v1/property/comparables.json
```

Cotality's published collection demonstrates four rule sets against this one operation:

| Rule | Use it for |
|---|---|
| RP Data Generic Rules | general comparable selection, with `returnFields` control |
| RP Data Sales Rule | comparable **sold** properties, with stats and detail |
| RP Data Listings For Sale Rule | comparable **current for-sale** listings |
| RP Data Listings For Rent Rule | comparable **current rental** listings |

For a geographic rather than rule-driven comparable set, use the sales searches — by bounding box
(`polygonPoints` as pipe-separated `lat|lon` pairs), locality, postcode or street — and filter with
`propertyTypes`, `fromDate`/`toDate`, `limit`/`offset` and `sort=contractdate.desc`.

## Rules that will bite you

- **No idempotency contract.** The live AVM POSTs carry no idempotency key. Treat a timeout as
  "unknown" and re-query the static AVM rather than blindly re-POSTing if duplicate compute is
  metered against you.
- **Valuation is a licensed output.** Cotality's disclaimers must be displayed alongside any value
  you surface; fetch them from the Content API and note they are unavailable in the sandbox.
- **PSX is a different product.** If you need a *human* valuation rather than a model estimate,
  that is the PSX valuation ordering exchange (panel lookup, quote, order, notifications,
  retrieval), documented at <https://developer.corelogic.asia/guides/psx-implementation> — not the
  AVM API.
