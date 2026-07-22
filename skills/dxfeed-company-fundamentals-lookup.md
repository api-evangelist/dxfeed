---
name: Look up company fundamentals for a symbol
description: Pull the most recent company profile, valuation ratios, financial statements, and earnings for a ticker symbol from the dxFeed Fundamentals API.
api: openapi/dxfeed-fundamentals-openapi.json
operations: [getRecentSymbol_23, getRecentSymbol, getRecentSymbol_12, getRecentSymbol_25, getRecentSymbol_24, getRecentSymbol_15]
generated: '2026-07-22'
method: generated
---

# Look up company fundamentals for a symbol

Base URL: `https://tools.dxfeed.com/fs` (production is entitlement-gated — dxFeed issues login/password credentials at onboarding; expect `403` without entitlements). Every operation declares `Accept-Encoding` as a required header — send `Accept-Encoding: gzip`.

## Steps

1. **Company identity** — `GET /v0.1/company-profile/recent/symbol/{symbol}` (`getRecentSymbol_23`). Returns the most recent profile record(s); note the `sid` (security id) and `cid` (company id) fields — they are the join keys across every fundamentals dataset.
2. **Valuation** — `GET /v0.1/valuation-ratio/recent/symbol/{symbol}` (`getRecentSymbol`) for P/E, P/B, and related ratios.
3. **Financial statements** — fetch the three statements for the same symbol:
   - `GET /v0.1/income-statement/recent/symbol/{symbol}` (`getRecentSymbol_12`)
   - `GET /v0.1/balance-statement/recent/symbol/{symbol}` (`getRecentSymbol_25`)
   - `GET /v0.1/cash-flow-statement/recent/symbol/{symbol}` (`getRecentSymbol_24`)
4. **Earnings** — `GET /v0.1/earning/recent/symbol/{symbol}` (`getRecentSymbol_15`).
5. Optionally pass `sources` (query, array) to pin the data source (Morningstar vs Borsa Istanbul).

## Rules

- Responses are JSON arrays of dataset records; an empty array means no coverage for that symbol, not an error.
- Errors use the custom `ApiError` envelope `{httpStatus, timestamp, messages[], exMessage}` — see `errors/dxfeed-problem-types.yml`. `403` = missing entitlement for that dataset; `406` = fix your Accept/Accept-Encoding headers.
- All reads are safe/idempotent GETs; there is no idempotency-key contract (see `conventions/dxfeed-conventions.yml`).
- Do not call the admin `addManualCorrection`/`addManualRemove` operations — they mutate vendor data and are for dxFeed operators.
