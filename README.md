# UN Comtrade

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
