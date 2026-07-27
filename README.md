# EPCOR (epcor)

EPCOR Utilities Inc. is a municipally owned Canadian utility headquartered in Edmonton, Alberta, wholly owned by the City of Edmonton, that builds and operates electricity distribution and transmission, water and wastewater, and natural gas distribution systems across Alberta, Ontario and British Columbia in Canada and in Arizona, New Mexico and Texas in the United States. In its Alberta home market it is both a wires company for Edmonton and, through EPCOR Energy Alberta, a regulated-rate electricity retailer, sitting at the distribution-and-retail end of the value chain rather than in generation (generation was spun out as Capital Power in 2009). Its API posture is defined entirely by regulation and nothing else: epcor.com publishes no developer portal, no API documentation and no machine-readable contracts, and the developer., developers., api., docs. and data. subdomains do not resolve. The one programmatic consumer surface is the Green Button implementation its three Ontario service areas — natural gas in the Aylmer area and electricity in the Collingwood and Kincardine areas — are required to run under Ontario's energy data regulation (O. Reg. 633/21), delivered as Download My Data behind a customer login and Connect My Data behind a third-party vendor registration portal, with EPCOR stating Green Button Alliance certification. Its far larger unmandated Alberta business publishes no equivalent, and EPCOR publishes no open grid or market data of its own — Alberta system and market data comes from AESO, not from EPCOR.

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

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### EPCOR Ontario Green Button (Download My Data / Connect My Data)

The Green Button energy-data service EPCOR operates for its three Ontario service areas (Aylmer-area natural gas, Collingwood-area and Kincardine-area electricity) to satisfy Ontario's O. Reg. 633/21. Download My Data lets an authenticated EPCOR customer download usage and billing data in an industry-standard XML format from the Green Button portal; Connect My Data ("Data Shares") lets a customer authorize a registered third-party vendor to receive energy usage data, billing data and/or account information on an ongoing basis via security tokens, with revocation from the portal's Data Shares tab. EPCOR states it has been certified by the Green Button Alliance. EPCOR publishes no technical documentation, no base URI, no ESPI/NAESB version reference and no machine-readable contract for this interface — a third party must apply through the vendor onboarding portal, and the customer-facing portal redirects every path to a login, so no endpoint could be verified anonymously. Not offered in EPCOR's Alberta or US service areas.

- **Human URL:** [https://www.epcor.com/ca/en/on/collingwood-area/account/manage-account/green-button.html](https://www.epcor.com/ca/en/on/collingwood-area/account/manage-account/green-button.html)
- **Base URL:** not published

#### Tags

- Energy
- Green Button
- Consumer Data
- Electricity
- Natural Gas
- Ontario

#### Properties

- [Documentation](https://www.epcor.com/ca/en/on/collingwood-area/account/manage-account/green-button.html)
- [Documentation](https://www.epcor.com/ca/en/on/aylmer-area/account/manage-account/green-button.html)
- [Documentation](https://www.epcor.com/ca/en/on/kincardine-area/account/manage-account/green-button.html)
- [Portal](https://epcorgas.savagedata.com/)
- [Registration](https://epcorgasonboarding.savagedata.com/)
- [Standard](https://www.greenbuttonalliance.org/)
- [Regulation](https://www.oeb.ca/consumer-information-and-protection/green-button)

## Common Properties

- [Website](https://www.epcor.com/)
- [Website](https://www.epcor.com/ca/en.html)
- [Website](https://www.epcor.com/us/en.html)
- [LinkedIn](https://www.linkedin.com/company/epcor)
- [Portal](https://customerportal.epcor.com/app/)
- [StatusPage](https://outages.epcor.com/)
- [About](https://www.epcor.com/Pages/about-epcor-ontario.aspx)

## Mandate Posture

- **Mandate regime:** `green-button-ontario` — Ontario O. Reg. 633/21 requires Ontario electricity and natural gas utilities to offer Green Button Download My Data and Connect My Data, certified by the Green Button Alliance, by 1 November 2023. No Canadian federal energy data right exists; Alberta has no equivalent.
- **Mandate status:** `live-implemented` — two live, EPCOR-branded production hosts were confirmed (a customer Green Button portal at `epcorgas.savagedata.com`, HTTP 200, and a third-party vendor registration application at `epcorgasonboarding.savagedata.com`, HTTP 200), both linked from EPCOR's own Green Button pages. Conformance itself is **attested, not observed**: no ESPI base URI, OAuth endpoint or `ApplicationInformation` resource could be read anonymously, and the Green Button Alliance certified-product register returned HTTP 403 to this probe.
- **Data standard:** Green Button (DMD + CMD). EPCOR names no version and never cites ESPI, NAESB or REQ.21; the regulation itself requires NAESB REQ.21 ESPI 3.3.
- **Consumer data:** available — but only in the three Ontario service areas, gated by customer consent and vendor registration. `/ca/en/ab/edmonton/account/manage-account/green-button.html` returns 404: the Alberta home market has no equivalent.
- **Market data:** none. No open grid, system or market data, no open data portal, no data licence. The public outage map at `outages.epcor.com` is an ArcGIS web app with no documented feed. Alberta market data comes from AESO, Ontario's from IESO.
- **Access gate:** `application-approval` for Connect My Data (register as an authorized third-party vendor, then obtain per-customer consent); `customer-account-required` for Download My Data. No self-serve path, no API keys, no public technical documentation.

See [review.yml](review.yml) for every URL probed, its HTTP status, and the full mandate/standard/access findings.
