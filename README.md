# EPCOR

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

EPCOR Utilities Inc. is a municipally owned Canadian utility headquartered in Edmonton, Alberta, wholly owned by the City of Edmonton, that builds and operates electricity distribution and transmission, water and wastewater, and natural gas distribution systems across Alberta, Ontario and British Columbia in Canada and in Arizona, New Mexico and Texas in the United States. In its Alberta home market it is both a wires company for Edmonton and, through EPCOR Energy Alberta, a regulated-rate electricity retailer, sitting at the distribution-and-retail end of the value chain rather than in generation (generation was spun out as Capital Power in 2009). EPCOR runs no developer programme: epcor.com publishes no developer portal, no API documentation, no OpenAPI and no llms.txt, and the developer., developers., api., docs. and data. subdomains do not resolve. It nonetheless operates two real programmatic surfaces. The first is compelled: the Green Button Download My Data and Connect My Data service its three Ontario service areas - natural gas in the Aylmer area and electricity in the Collingwood and Kincardine areas - must run under Ontario's energy data regulation (O. Reg. 633/21), delivered behind a customer login and a third-party vendor registration portal, with EPCOR stating Green Button Alliance certification but publishing no base URI, no ESPI version and no technical contract. The second is accidental and entirely open: a public ArcGIS Online organization (owner epcor_outages) whose 36 production feature services - Edmonton power outage areas, Canadian water main breaks, water infrastructure projects, scheduled field events, and the outage and service-area layers for fourteen EPCOR Water USA districts in Arizona and New Mexico - answer anonymous ArcGIS REST queries with live data. EPCOR documents none of it, licenses none of it and announces none of it. The result is a utility that is open where a province compelled it, open where nobody noticed, and closed everywhere it would count as a product; wholesale market and system data still comes from AESO and IESO, not from EPCOR.

**Areas:** Energy · Canada · Utilities · Electricity · Natural Gas · Water · Green Button · Smart Metering · Grid · Ontario · Alberta · Outages

## EPCOR on APIs.io

Everything profiled for EPCOR is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/epcor/](https://apis.io/providers/epcor/)** — or go straight to one of the APIs or properties below.

### APIs (8)

- [EPCOR Ontario Green Button (Download My Data / Connect My Data)](https://apis.io/apis/epcor/epcor-ontario-green-button/) — The Green Button energy-data service EPCOR operates for its three Ontario service areas (Aylmer-area natural gas, Collingwood-area and Kincardine-area…
- [EPCOR Boundaries API](https://apis.io/apis/epcor/epcor-boundaries-api/) — Municipal boundary reference layers.
- [EPCOR Catalog API](https://apis.io/apis/epcor/epcor-catalog-api/) — Service directory.
- [EPCOR Infrastructure API](https://apis.io/apis/epcor/epcor-infrastructure-api/) — Water infrastructure construction projects.
- [EPCOR Power Outages API](https://apis.io/apis/epcor/epcor-power-outages-api/) — Edmonton electricity distribution outages (active, planned and point features).
- [EPCOR Service Areas API](https://apis.io/apis/epcor/epcor-service-areas-api/) — EPCOR Water USA service area boundaries.
- [EPCOR Us Water Outages API](https://apis.io/apis/epcor/epcor-us-water-outages-api/) — EPCOR Water USA district outage points (Arizona and New Mexico).
- [EPCOR Water Outages API](https://apis.io/apis/epcor/epcor-water-outages-api/) — Canadian water outages, main breaks and field events.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Epcor Agentic Access](https://apis.io/agentic-access/epcor/epcor-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [EPCOR public feature layer attributes](https://apis.io/schemas/epcor/epcor-outage-features.schema/)

#### Examples (6)

Example requests and responses.

- [Epcor Arcgis Error Responses](https://apis.io/examples/epcor/epcor-arcgis-error-responses/)
- [Epcor Arcgis Service Directory](https://apis.io/examples/epcor/epcor-arcgis-service-directory/)
- [Epcor Outage Map Config](https://apis.io/examples/epcor/epcor-outage-map-config/)
- [Epcor Power Outage Areas Geojson](https://apis.io/examples/epcor/epcor-power-outage-areas-geojson/)
- [Epcor Power Outage Areas Query](https://apis.io/examples/epcor/epcor-power-outage-areas-query/)
- [Epcor Water Canada Outages Query](https://apis.io/examples/epcor/epcor-water-canada-outages-query/)

#### Collections (1)

Postman and Open Collection request collections.

- [EPCOR Public Outage and Service Area Feature Services (ArcGIS REST)](https://apis.io/collections/epcor/open-epcor-outages-arcgis/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Epcor Authentication](https://apis.io/security/epcor/epcor-authentication/)
- [Epcor Domain Security](https://apis.io/security/epcor/epcor-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.epcor.com/)
- [Support](https://www.epcor.com/ca/en/ab/edmonton/contact-edmonton.html)
- [Blog](https://www.epcor.com/ca/en/news.html)
- [Terms of service](https://www.epcor.com/ca/en/about/policies/terms-of-use.html)
- [Privacy policy](https://www.epcor.com/ca/en/about/policies/privacy-policy.html)
- [Status](https://outages.epcor.com/)

## API Evangelist rating

**Kin Score 32.9** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 64.3 |
| Contract quality | 16.8 |
| Contract governance | 18.2 |
| Operational transparency | 15.8 |
| Developer ergonomics | 39.9 |
| Access clarity | 34.2 |

**Agent readiness 25.8** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 34.8** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/epcor/](https://apis.io/providers/epcor/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for EPCOR: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/epcor/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
