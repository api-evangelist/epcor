---
name: Map EPCOR Water USA districts and outages
description: Enumerate EPCOR Water's US service territories in Arizona and New Mexico and read live district outage points from the public ArcGIS feature services.
api: openapi/epcor-outages-arcgis-openapi.yml
operations:
  - listFeatureServices
  - queryServiceAreasAguaFriaProd
  - queryServiceAreasMohaveProd
  - queryServiceAreasSunCityProd
  - queryUsaChaparralOutagesProd
  - queryUsaSuncityOutagesProd
  - queryUsaAguaFriaOutagesProd
generated: '2026-07-27'
method: generated
source: derived from openapi/epcor-outages-arcgis-openapi.yml, which was itself derived from live ArcGIS metadata
---

# Map EPCOR Water USA districts and outages

EPCOR's US water business is published as a per-district pair of public ArcGIS feature services: a service
area polygon and an outage point layer. Anonymous GETs, no key.

## The districts

Fourteen outage services and thirteen service-area services exist, one per district:
Agua Fria, Anthem, Chaparral, Clovis (NM), Edgewood (NM), Havasu, Mohave, North Mohave Valley,
Paradise Valley, Sun City, Sun City West, Thunder Mountain, Tubac, Willow Valley (outages only).

Operation naming follows the service names exactly:

- service areas: `queryServiceAreas<District>Prod` - e.g. `queryServiceAreasAguaFriaProd`,
  `queryServiceAreasSunCityWestProd`, `queryServiceAreasNorthMohaveValleyProd`
- outages: `queryUsa<District>OutagesProd` - e.g. `queryUsaChaparralOutagesProd`,
  `queryUsaSuncityOutagesProd`, `queryUsaNorthmohavevalleyOutagesProd`

The two families capitalise differently (`SunCityWest` vs `Suncitywest`). Enumerate with
`listFeatureServices` rather than constructing names by hand.

## Steps

1. `listFeatureServices` and filter for names matching `^ServiceAreas_.*_prod$` and `^usa_.*_outages_prod$`.
   Ignore the `_dev`, `_test`, `_ist` and `_uat` copies - EPCOR publishes its whole environment pipeline in
   the same public folder, and only `_prod` is a consumer surface.
2. **Footprint:** call a service-area query with `where=1=1&outFields=*&f=geojson`. Fields:
   `ServiceAre`, `District`, `State`, `Shape_Leng`, `Shape_Area`. This is the closest thing EPCOR publishes
   to an operating-territory dataset.
3. **Outages:** call the matching district outage query with `where=1=1&outFields=*&f=json`. The US record is
   materially richer than the Canadian one (21 fields):
   - `FaultID`, `CommunityI` / `CommunityN`, `ConditionI` / `ConditionN`
   - `Planned` - planned vs unplanned flag
   - `ApproxArea`, `Details`
   - `ReportDate`, `EstimateRe`, `ActualRest` - **string** dates, same caveat as everywhere else
   - `MapX` / `MapY` plus full audit columns (`CreatedBy`, `CreatedDat`, `EditedBy`, `EditedDate`,
     `PublishBy`, `PublishDat`)
4. **Aggregate across districts** by iterating the 14 outage services; there is no single national layer and
   no cross-district identifier. Most districts sit at zero features most of the time - use
   `returnCountOnly=true` for a cheap sweep before pulling attributes.

## Rules

- Check the body for an `error` object even on HTTP 200.
- Page with `resultRecordCount` / `resultOffset` when `exceededTransferLimit` is true.
- Nothing about this surface is documented, licensed or guaranteed by EPCOR. Cache what you pull and degrade
  gracefully if a service name disappears.
