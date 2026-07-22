---
name: Screen fundamentals across markets by date range
description: Query dxFeed Fundamentals datasets in bulk with date-range, symbol, country, currency, and industry filters — e.g. IPO calendars, economic calendars, or valuation screens.
api: openapi/dxfeed-fundamentals-openapi.json
operations: [getDeepFilter, getDeepFilter_7, getDeepFilter_14, getDeepFilter_23]
generated: '2026-07-22'
method: generated
---

# Screen fundamentals across markets by date range

Base URL: `https://tools.dxfeed.com/fs` (entitlement-gated in production). Every fundamentals dataset exposes the same `/filter` resource; the pattern below works across all ~28 datasets.

## Steps

1. Pick the dataset and call its filter operation with the **required** `fromYmd` and `toYmd` date-range params (YYYYMMDD strings):
   - Valuation screen — `GET /v0.1/valuation-ratio/filter` (`getDeepFilter`)
   - Upcoming IPOs — `GET /v0.1/ipo-calendar/filter` (`getDeepFilter_7`)
   - Macro events — `GET /v0.1/economic-calendar/filter` (`getDeepFilter_14`)
   - Company universe — `GET /v0.1/company-profile/filter` (`getDeepFilter_23`)
2. Narrow with the optional shared filters: `symbols[]`, `sids[]`, `cids[]`, `countryCode`, `currencyCode`, `sicCodes[]`, `industryCodes[]`, `mics[]` (exchange MICs), `sources[]`.
3. For large filter payloads use the sibling `POST /filter` operation instead of the GET query string.
4. Join results across datasets on `sid`/`cid` (see `data-model/dxfeed-data-model.yml`).

## Rules

- Keep `fromYmd`/`toYmd` windows tight — there is no pagination; the date range is the result-set bound (see `conventions/dxfeed-conventions.yml`).
- `Accept-Encoding` header is required on every operation; send `Accept-Encoding: gzip`.
- `400` = malformed filter (check ymd format); `403` = dataset not in your entitlements. Envelope: `ApiError` — see `errors/dxfeed-problem-types.yml`.
