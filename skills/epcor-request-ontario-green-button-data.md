---
name: Obtain EPCOR Ontario Green Button customer energy data
description: The real, non-technical procedure for getting a customer's EPCOR Ontario energy usage data - vendor registration plus per-customer consent. There is no public technical contract for this surface.
api: none-published
operations: []
generated: '2026-07-27'
method: generated
source: >-
  EPCOR's own Green Button pages for the Aylmer, Collingwood and Kincardine service areas, plus live probes of
  the portal and vendor onboarding hosts on 2026-07-27
---

# Obtain EPCOR Ontario Green Button customer energy data

**Read this first: there is nothing to call.** EPCOR publishes no base URI, no endpoint, no OAuth metadata,
no ESPI/NAESB version and no machine-readable contract for its Green Button implementation. This skill exists
so an agent does not invent one. Every technical detail below was observed, not documented, and the paths that
would normally carry a contract (`/.well-known/openid-configuration`,
`/espi/1_1/resource/ApplicationInformation`, `/DataCustodian/oauth/authorize`) all return the login
single-page app.

## Scope

Only three EPCOR service areas offer this, because Ontario compelled it under O. Reg. 633/21:

- Aylmer area - natural gas
- Collingwood area - electricity
- Kincardine area - electricity

EPCOR's much larger Alberta business has no equivalent (`/ca/en/ab/edmonton/account/manage-account/green-button.html`
returns 404), and the US water utilities have none.

## If you are the customer (Download My Data)

1. Log in to the EPCOR Green Button portal at `https://epcorgas.savagedata.com/` (every path redirects to
   `/Connect/Authorize`).
2. Select and download usage and billing data in the Green Button XML format.
3. There is no anonymous or programmatic path to this file. Do not attempt to construct one.

## If you are a third party (Connect My Data)

1. Apply as an authorized vendor through `https://epcorgasonboarding.savagedata.com/` (a Blazor registration
   application; it disclosed no technical requirements when probed, and rendered an error).
2. Wait for EPCOR to approve the registration. There is no self-serve path and no API key.
3. For each customer, send them to your own Green Button registration page; they are redirected to EPCOR to
   authenticate and choose what to share:
   - Energy Usage Data
   - Billing Data
   - Account Information
4. Data then flows to you on an ongoing basis "using security tokens" (EPCOR's phrasing - it never says
   OAuth), until the customer revokes the share from the **Data Shares** tab in the portal.

## What to record, honestly

- EPCOR states it "has been certified by the Green Button Alliance". The Alliance's certified-product
  register returned HTTP 403 to our probe, so that claim is attested, not independently verified.
- The regulation requires NAESB REQ.21 ESPI 3.3 underneath. EPCOR names no version, no standard and no schema
  anywhere public. Do not assume a specific ESPI resource layout until EPCOR's onboarding pack confirms it.
- Ask EPCOR directly, during vendor onboarding, for: the ESPI base URI, the authorization and token
  endpoints, the ESPI version, the ApplicationInformation resource, and the scope/`DataCustodian` model.
  Those are the five things missing from the public record.

## Related

- `authentication/epcor-authentication.yml` - what was and was not verifiable about this auth model
- `conformance/epcor-conformance.yml` - the regulatory and standards posture
- `review.yml` - every URL probed with its HTTP status
