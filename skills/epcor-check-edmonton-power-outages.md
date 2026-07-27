---
name: Check EPCOR Edmonton power outages
description: Read live and planned electricity outages in EPCOR's Edmonton distribution territory from the public ArcGIS feature services that back the EPCOR outage map - no credential required.
api: openapi/epcor-outages-arcgis-openapi.yml
operations:
  - listFeatureServices
  - getOcpsProdAvService
  - queryOcpsProdAv
  - queryOcpsProdPl
  - queryCityBoundaryProd
generated: '2026-07-27'
method: generated
source: derived from openapi/epcor-outages-arcgis-openapi.yml, which was itself derived from live ArcGIS metadata
---

# Check EPCOR Edmonton power outages

EPCOR has no developer portal and no API keys. Its Edmonton outage data is published as public ArcGIS
feature services under `https://services6.arcgis.com/Ji2rusuWXDFSqNsP/ArcGIS/rest/services`, readable
anonymously over plain GETs.

## Before you start

- **No authentication.** Do not send a key or token; none exists for reading.
- **Errors come back as HTTP 200.** Always inspect the body for an `error` object before treating a response
  as data (see `errors/epcor-problem-types.yml`).
- **Nothing here is licensed.** EPCOR publishes no terms of use, licence or attribution requirement for this
  surface, and no availability commitment. Treat it as best effort.

## Steps

1. **Confirm the surface exists.** Call `listFeatureServices` (`GET /?f=json`) and check that
   `ocps_prod_av` and `ocps_prod_pl` are present. Service names have changed generations before -
   `power_outage_prod` is an older, now-empty point service still published alongside them.
2. **Read the contract before the data.** Call `getOcpsProdAvService` (`GET /ocps_prod_av/FeatureServer?f=json`)
   to confirm `maxRecordCount` (2000) and the layer list.
3. **Pull active outages.** Call `queryOcpsProdAv` with `where=1=1`, `outFields=*`, `f=json`. Each feature is
   one active outage area with:
   - `id` - EPCOR incident number, e.g. `INC 218006057`
   - `cause`, `affcusts` (affected customer count, a **string**), `nbhoods`, `affstree`
   - `faulted` (fault start) and `estresto` (estimated restoration)
4. **Page properly.** If the response sets `exceededTransferLimit: true`, re-request with
   `resultRecordCount=2000` and an incrementing `resultOffset`. There is no cursor.
5. **Pull planned outages** the same way with `queryOcpsProdPl`; its fields differ (`startat`, `endat`,
   `details`, `lastupd`). This layer is frequently empty - zero features is a normal answer, not a failure.
6. **Add a map frame if you need one** with `queryCityBoundaryProd`.

## Parsing rules that will bite you

- `estresto`, `faulted`, `startat` and `endat` are **free-text local display strings with no year and no
  timezone** (`"Jul-27 5:30 PM"`). They are not epoch dates. Resolve the year against the time you fetched,
  in Mountain Time, and treat any inference as approximate.
- `affcusts` is a string, not a number. Cast it defensively.
- `Shape__Area` / `Shape__Length` are null when `returnGeometry=false`.
- Use `returnGeometry=false` unless you need the polygon; the polygons are large.

## Cheap patterns

- Count only: `queryOcpsProdAv` with `returnCountOnly=true`.
- Map overlay: same call with `f=geojson` returns RFC 7946 straight to a mapping library.
- Neighbourhood filter: `where=nbhoods LIKE '%Parkview%'` (SQL-92 is fully supported).
