---
name: Pull Australian auction clearance rates and suburb market trends
description: >-
  Retrieve the weekly auction results and clearance rates the Australian property press runs on,
  and the suburb/locality market-trend and census statistics behind them — as JSON, or as a
  server-rendered chart image.
api: CoreLogic Australia Auction API + Statistics API + Charts API
grounding: collections/corelogic-au-sample-sandbox.postman_collection.json
generated: '2026-07-26'
method: generated
operations:
  - GET /au/summaries/state/{state}
  - GET /au/results/state/{state}
  - GET /au/results/state/{state}/weeks/{n}
  - GET /au/results/state/{state}/search
  - GET /au/results/state/{state}/compare/years/{n}
  - GET /au/details/state/{state}/postcode/{postcode}/suburb/{suburb}
  - POST /v1/statistics.json
  - GET /census/summary
  - POST /census
  - GET /v2/chart.png
  - GET /census
  - GET /legal/disclaimers/{key}
---

# Auction clearance rates and market trends

Hold a bearer token first — see `corelogic-au-authenticate-and-call.md`.

## Auction results — `https://auction.api.cotality.com.au`

State codes are lower-case two-letter Australian states (`qld`, `nsw`, `vic`, `sa`, `wa`, `tas`,
`nt`, `act`).

```
GET /au/summaries/state/qld?capitalCityOnly=true          # latest state summary
GET /au/results/state/qld                                 # latest results, whole state
GET /au/results/state/qld?capitalCityOnly=true            # capital city only
GET /au/results/state/nsw?capitalCityOnly=true&stats=clearance-rate
GET /au/results/state/qld/weeks/2                         # last N weeks
GET /au/results/state/qld/search?fromDate=2018-01-01&toDate=2019-01-01
GET /au/results/state/qld/compare/years/2                 # year-on-year comparison
GET /au/details/state/qld/postcode/4116/suburb/CALAMVALE  # suburb-level detail
```

`capitalCityOnly=true` is the switch between the state figure and the capital-city figure — the
two are routinely different, and quoting the wrong one is the most common reporting error on this
dataset. `stats=clearance-rate` returns the clearance statistic rather than the result list.

**Always attach the disclaimer.** The auction dataset has its own disclaimer keys:

```
GET https://content.api.cotality.com.au/legal/disclaimers/auction_au
GET https://content.api.cotality.com.au/legal/disclaimers/auction_standalone_au
```

Use `auction_standalone_au` when the clearance rate is published on its own rather than inside a
wider Cotality data display.

## Market statistics — `https://statistics.api.cotality.com.au`

```
POST /v1/statistics.json                                   # market trends by location + metric
GET  /census/summary?locationId=14489&locationTypeId=8      # ABS census summary
POST /census                                               # census statistics
```

Everything is keyed on a **location identifier plus a location-type identifier**
(`locationId`/`locationTypeId`, or `lId`/`lTId` on the chart surface) and a **metric-type
identifier**. Resolve location ids through Suggest or Address Matcher; the metric vocabulary is
documented at <https://developer.corelogic.asia/guides/metric-types>.

## Charts — `https://charts.api.cotality.com.au`

The Charts API returns `image/png`, not JSON. Series are numbered `s1`, `s2`, … and each carries
its own location, property type and metric:

```
GET /v2/chart.png?chartSize=400x700&fromDate=2014-01-01&toDate=2017-01-01
    &s1.lId=12606&s1.lTId=8&s1.pTId=2&s1.mTId=21
    &s2.lId=3723&s2.lTId=8&s2.pTId=2&s2.mTId=21

GET /census?s1.lTId=8&metricTypeGroupId=120&chartSize=500x500&s1.lId=12606
```

Presentation parameters (`backgroundColor`, `chartColors`, `titleValue`, `titleAlign`,
`gridLineDashStyle`, `markerRadius`, `lineWidth`, `yAxisTitleValue`, `xAxisTitleValue`,
`legendEnabled`, `dataLabelFormat`, `creditsValue`) let you theme the image server-side — see
<https://developer.corelogic.asia/guides/charts-customisation>.

## Sandbox limits to expect

Market-trend data in the sandbox covers only the **past three years** for suburb, postcode, local
government area and territory authority, and **one year** for state and country, drawn from the
same 29 suburbs as the property data. Historical auction searches beyond that window will come
back empty in the sandbox and are not a bug.
