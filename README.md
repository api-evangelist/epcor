# EPCOR (epcor)

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
