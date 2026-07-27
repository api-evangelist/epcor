# EPCOR (epcor)

EPCOR Utilities Inc. is a municipally owned Canadian utility headquartered in Edmonton, Alberta, wholly owned by the City of Edmonton, that builds and operates electricity distribution and transmission, water and wastewater, and natural gas distribution systems across Alberta, Ontario and British Columbia in Canada and in Arizona, New Mexico and Texas in the United States. In its Alberta home market it is both a wires company for Edmonton and, through EPCOR Energy Alberta, a regulated-rate electricity retailer, sitting at the distribution-and-retail end of the value chain rather than in generation (generation was spun out as Capital Power in 2009).

EPCOR runs no developer programme — no developer portal, no API documentation, no OpenAPI, no llms.txt, and the developer., developers., api., docs. and data. subdomains do not resolve. It nonetheless operates **two real programmatic surfaces**:

1. **Compelled** — the Green Button Download My Data and Connect My Data service its three Ontario service areas (Aylmer-area natural gas, Collingwood-area and Kincardine-area electricity) must run under Ontario's O. Reg. 633/21. Gated behind a customer login and a third-party vendor registration portal, with EPCOR stating Green Button Alliance certification but publishing no base URI, no ESPI version and no technical contract.
2. **Accidental and entirely open** — a public ArcGIS Online organization (item owner `epcor_outages`) whose 36 production feature services answer anonymous ArcGIS REST queries with live operational data: Edmonton power outage areas, Canadian water main breaks, water infrastructure projects, scheduled field events, and outage plus service-area layers for fourteen EPCOR Water USA districts in Arizona and New Mexico. EPCOR documents none of it, licenses none of it and announces none of it.

Wholesale market and system data still comes from AESO and IESO, not from EPCOR.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/epcor/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/epcor/refs/heads/main/apis.yml)

## Tags

- Energy
- Canada
- Utilities
- Electricity
- Natural Gas
- Water
- Green Button
- Smart Metering
- Grid
- Ontario
- Alberta
- Outages
- Geospatial
- Open Data

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### EPCOR Ontario Green Button (Download My Data / Connect My Data)

The Green Button energy-data service EPCOR operates for its three Ontario service areas to satisfy Ontario's O. Reg. 633/21. Download My Data lets an authenticated EPCOR customer download usage and billing data in an industry-standard XML format; Connect My Data ("Data Shares") lets a customer authorize a registered third-party vendor to receive energy usage data, billing data and/or account information on an ongoing basis via security tokens, revocable from the portal's Data Shares tab. EPCOR publishes no technical documentation, no base URI, no ESPI/NAESB version reference and no machine-readable contract — a third party must apply through the vendor onboarding portal, and the customer-facing portal redirects every path to a login. Not offered in EPCOR's Alberta or US service areas.

- **Human URL:** [https://www.epcor.com/ca/en/on/collingwood-area/account/manage-account/green-button.html](https://www.epcor.com/ca/en/on/collingwood-area/account/manage-account/green-button.html)
- **Base URL:** not published

### EPCOR Public Outage and Service Area Feature Services (ArcGIS REST)

EPCOR's undocumented but fully public geospatial data surface, discovered in the 2026-07-27 enrichment round by following the outage map's bundle to `/assets/config.json`. Thirty-six production feature services answer anonymous queries with live data — no API key, no signup, no rate limit, no licence, no terms of use and no support channel. Format is chosen with `f` (json / geojson / pbf), paging uses `resultOffset` / `resultRecordCount` against a 2000-feature cap, and errors come back with **HTTP 200** and an Esri error body.

- **Human URL:** [https://outages.epcor.com/](https://outages.epcor.com/)
- **Base URL:** `https://services6.arcgis.com/Ji2rusuWXDFSqNsP/ArcGIS/rest/services`
- **Derived OpenAPI:** [openapi/epcor-outages-arcgis-openapi.yml](openapi/epcor-outages-arcgis-openapi.yml) — 115 read operations over 39 production layers, derived from live ArcGIS metadata. **Not published by EPCOR.**

## Artifacts

| Artifact | File |
|---|---|
| OpenAPI (derived) | [openapi/epcor-outages-arcgis-openapi.yml](openapi/epcor-outages-arcgis-openapi.yml) |
| JSON Schema (derived) | [json-schema/epcor-outage-features.schema.json](json-schema/epcor-outage-features.schema.json) |
| Examples (verbatim captures) | [examples/](examples/) |
| Authentication | [authentication/epcor-authentication.yml](authentication/epcor-authentication.yml) |
| Conventions | [conventions/epcor-conventions.yml](conventions/epcor-conventions.yml) |
| Error catalog | [errors/epcor-problem-types.yml](errors/epcor-problem-types.yml) |
| Lifecycle | [lifecycle/epcor-lifecycle.yml](lifecycle/epcor-lifecycle.yml) |
| Conformance | [conformance/epcor-conformance.yml](conformance/epcor-conformance.yml) |
| Data model | [data-model/epcor-data-model.yml](data-model/epcor-data-model.yml) |
| Domain security | [security/epcor-domain-security.yml](security/epcor-domain-security.yml) |
| Well-known probes (all misses) | [well-known/epcor-well-known.yml](well-known/epcor-well-known.yml) |
| Packages (none) | [packages/epcor-packages.yml](packages/epcor-packages.yml) |
| Agentic access | [agentic-access/epcor-agentic-access.yml](agentic-access/epcor-agentic-access.yml) |
| Agent skills | [skills/_index.yml](skills/_index.yml) |
| llms.txt (generated) | [llms/epcor-llms.txt](llms/epcor-llms.txt) |

## Mandate Posture

- **Mandate regime:** `green-button-ontario` — Ontario O. Reg. 633/21 requires Ontario electricity and natural gas utilities to offer Green Button Download My Data and Connect My Data, certified by the Green Button Alliance, by 1 November 2023. No Canadian federal energy data right exists; Alberta has no equivalent.
- **Mandate status:** `live-implemented` — two live, EPCOR-branded production hosts were confirmed (a customer Green Button portal at `epcorgas.savagedata.com`, HTTP 200, and a third-party vendor registration application at `epcorgasonboarding.savagedata.com`, HTTP 200), both linked from EPCOR's own Green Button pages. Conformance itself is **attested, not observed**: no ESPI base URI, OAuth endpoint or `ApplicationInformation` resource could be read anonymously, and the Green Button Alliance certified-product register returned HTTP 403 to this probe.
- **Data standard:** Green Button (DMD + CMD). EPCOR names no version and never cites ESPI, NAESB or REQ.21; the regulation itself requires NAESB REQ.21 ESPI 3.3.
- **Consumer data:** available — but only in the three Ontario service areas, gated by customer consent and vendor registration. `/ca/en/ab/edmonton/account/manage-account/green-button.html` returns 404: the Alberta home market has no equivalent.
- **Market data:** none. No wholesale grid, system or market data, no open data portal, no data licence. Alberta market data comes from AESO, Ontario's from IESO.
- **Operational data:** open, unannounced and unlicensed — the ArcGIS feature services above. This corrects the first round's finding that the outage map was "a map, not a dataset".
- **Access gate:** `application-approval` for Connect My Data (register as an authorized third-party vendor, then obtain per-customer consent); `customer-account-required` for Download My Data; **none at all** for the ArcGIS surface.

See [review.yml](review.yml) for every URL probed, its HTTP status, and the full mandate/standard/access findings.
