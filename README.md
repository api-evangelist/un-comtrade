# UN Comtrade

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

United Nations international trade statistics database with a REST API for accessing import/export data, commodity trade flows, and bilateral trade statistics.

## Overview

UN Comtrade is the world's most comprehensive trade data repository, maintained by the United Nations Statistics Division. It covers international merchandise and services trade statistics for over 200 reporting countries and territories, with data going back to 1962 for many reporters. Commodity data is classified using HS (Harmonized System), SITC (Standard International Trade Classification), and other recognized schemes.

## API Access

The UN Comtrade API is available at `https://comtradeapi.un.org` and is managed through the [UN Comtrade Developer Portal](https://comtradedeveloper.un.org/).

### Authentication

- **No key required:** Public preview endpoints, limited to 500 records per call
- **Free API key:** Register at [comtradeplus.un.org](https://comtradeplus.un.org/), then subscribe to the free product on the Developer Portal. Provides 500 calls/day with up to 100,000 records per call.
- **Premium key:** Annual subscription starting at $2,000/year for individuals. Unlocks bulk downloads, async batch processing (up to 2.5M records), and higher call limits.

API keys are passed as the `Ocp-Apim-Subscription-Key` request header or as the `subscription-key` query parameter.

## Key Endpoints

| Endpoint | Description | Auth Required |
|---|---|---|
| `GET /public/v1/preview/{type}/{freq}/{cl}` | Preview trade data (500 records max) | No |
| `GET /data/v1/get/{type}/{freq}/{cl}` | Extract final trade data | Yes |
| `GET /data/v1/getTariffline/{type}/{freq}/{cl}` | Extract tariffline data | Yes |
| `GET /data/v1/getDa/{type}/{freq}/{cl}` | Data availability | Yes |
| `GET /data/v1/getMetadata` | Reference metadata | Yes |
| `GET /data/v1/getLiveUpdate` | Recent publications | Yes |
| `GET /bulk/v1/get/{type}/{freq}/{cl}` | Bulk file links | Premium |
| `GET /bulk/v1/getTariffline/{type}/{freq}/{cl}` | Bulk tariffline files | Premium |
| `GET /bulk/v1/getClassic/{type}/{freq}/{cl}` | Classic format bulk files | Premium |

### Path Parameters

- `{type}`: `C` (Goods) or `S` (Services)
- `{freq}`: `A` (Annual) or `M` (Monthly)
- `{cl}`: Classification code — `HS`, `H5`, `H4`, `H3`, `S3`, `S2`, `S1`

## Subscription Plans

| Plan | Annual Cost | Calls/Day | Records/Call |
|---|---|---|---|
| Free Preview | $0 | Unlimited | 500 |
| Free Registered | $0 | 500 | 100,000 |
| Premium Individual | $2,000 | 5,000 | 250,000 |
| Premium Institutional Pro 1 (non-profit/academic) | $6,000 | Unlimited | 250,000 |
| Premium Institutional Pro 2 (private sector) | $12,000 | Unlimited | 250,000 |

Trial subscriptions are available. Contact [subscriptions@un.org](mailto:subscriptions@un.org).

## SDKs and Libraries

- **Python:** [comtradeapicall](https://github.com/uncomtrade/comtradeapicall) — `pip install comtradeapicall`
- **R:** [comtradr](https://docs.ropensci.org/comtradr/) — available on CRAN

## Resources

- [Developer Portal](https://comtradedeveloper.un.org/)
- [Documentation](https://uncomtrade.org/docs/)
- [Data Platform](https://comtradeplus.un.org/)
- [Subscription Pricing](https://shop.un.org/databases)
- [API Key Guide](https://uncomtrade.org/docs/api-subscription-keys/)

## Contact

- General support: [comtrade@un.org](mailto:comtrade@un.org)
- Subscriptions: [subscriptions@un.org](mailto:subscriptions@un.org)
