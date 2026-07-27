---
name: Track EPCOR water outages, main breaks and infrastructure projects
description: Read Canadian water main breaks, water events and the water capital project pipeline from EPCOR's public ArcGIS feature services.
api: openapi/epcor-outages-arcgis-openapi.yml
operations:
  - queryEPCorWaterOutagesProd
  - queryWaterCanadaOutagesProd
  - queryGenericWaterEventsProdL0
  - queryGenericWaterEventsProdL1
  - queryUDFEventsProdL0
  - queryWaterInfrastructureProjectsProdL0
  - queryWaterInfrastructureProjectsProdL1
generated: '2026-07-27'
method: generated
source: derived from openapi/epcor-outages-arcgis-openapi.yml, which was itself derived from live ArcGIS metadata
---

# Track EPCOR water outages, main breaks and infrastructure projects

Everything below is anonymous GET traffic against
`https://services6.arcgis.com/Ji2rusuWXDFSqNsP/ArcGIS/rest/services`. No key, no signup, no rate limit is
published. Errors arrive as HTTP 200 with an `error` body.

## Water outages and main breaks

Two services carry the same record shape and both are live:

1. `queryEPCorWaterOutagesProd` - 9 fields, includes `TankLocati`.
2. `queryWaterCanadaOutagesProd` - 8 fields, no `TankLocati`.

Call each with `where=1=1&outFields=*&returnGeometry=false&f=json`. Key fields:

- `MainbreakI` - the break identifier, e.g. `MB4575`
- `Cause` - e.g. `Water Main Break`
- `ReportDate` - free text local display string, no year (`"Jan-30  7:34 PM"`)
- `Status` - a customer-facing narrative, not an enum. Do not pattern-match it as a state machine.
- `EstimateRe` - often carries a sentence such as `Customers are NOT out of Water` rather than a time.

De-duplicate across the two services on `MainbreakI` before counting; records persist for weeks after repair
while surface restoration is pending, so an open record does not mean an active service interruption.

## Other water events

- `queryGenericWaterEventsProdL0` (points) and `queryGenericWaterEventsProdL1` (areas) carry
  `Event`, `EventType`, `Location`, `Description` and **typed** `ApproximateStartDate` /
  `ApproximateEndDate` in epoch milliseconds - unlike the outage layers.
- `queryUDFEventsProdL0` carries scheduled field events with `UDFID`, `SCHD_START`, `SCHD_END` and a `URL`
  back to the EPCOR page describing the work. The area layer mirrors the point layer one for one.

## Infrastructure projects

`queryWaterInfrastructureProjectsProdL0` (points) and `...L1` (areas) are the richest dataset in the folder:
`PR_NUMBER`, `PR_NAME`, `PR_STATUS`, `PR_TYPE`, `PR_YEAR`, `LIFE_CYCLE`, typed `START_DATE` / `END_DATE`,
an `OVERVIEW` narrative and a `REDIRECT` link to the project page.

Useful queries:

- Current programme year: `where=PR_YEAR = 2026&outFields=*`
- Active work: `where=PR_STATUS <> 'Complete'`
- Server-side rollup: add `groupByFieldsForStatistics=PR_STATUS&outStatistics=[{"statisticType":"count",
  "onStatisticField":"PR_NUMBER","outStatisticFieldName":"n"}]` - the layers advertise
  `supportsStatistics`, so aggregate without pulling features.

## Rules

- Page with `resultRecordCount` (max 2000) + `resultOffset` whenever `exceededTransferLimit` is true.
- Prefer `f=geojson` for map rendering, `f=json` when you want the field definitions alongside the data.
- Treat every string date field as approximate; only the `*Date`/`SCHD_*`/`PR_*` typed fields are real
  timestamps (epoch milliseconds).
