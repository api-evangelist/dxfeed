# dxFeed (dxfeed)

dxFeed is a market data distributor and subsidiary of Devexperts, headquartered in Munich, delivering real-time, delayed, historical, and on-demand financial market data across equities, ETFs, futures, options, indices, FX, fixed income, and crypto (3.5M instruments, ~200,000 simultaneous streaming clients), plus reference data (instrument profiles, corporate actions, trading schedules), Morningstar-sourced fundamentals, options analytics, and news feeds. Delivery is developer-documented but sales-gated — production credentials (endpoint URLs, login, password) arrive via onboarding after contacting sales — across a REST web service with Server-Sent Events streaming, the dxLink WebSocket protocol (public AsyncAPI spec and live demo endpoint), a binary QD protocol over TCP, FIX, file-based historical/tick data extraction, and Java/C++/.NET/Swift/Go/JavaScript/Python client libraries.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/dxfeed/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/dxfeed/refs/heads/main/apis.yml)

## Tags

- Financial
- Market Data
- Real-Time
- Historical Data
- Equities
- Options
- Futures
- Crypto
- Reference Data
- Fundamentals

## Timestamps

- **Created:** 2026-07-21
- **Modified:** 2026-07-21

## APIs

### dxFeed REST Web Service API

REST service over the core dxFeed API with /events (snapshot), /eventSource (Server-Sent Events stream), /addSubscription, and /removeSubscription resources across 20+ market event types (Quote, Trade, Profile, Candle, Greeks, Order, Series) in JSON or XML. A public demo endpoint serves delayed data; production hosts and credentials are issued during sales onboarding.

- **Human URL:** [https://kb.dxfeed.com/en/market-data-api/data-access-solutions/rest.html](https://kb.dxfeed.com/en/market-data-api/data-access-solutions/rest.html)
- **Base URL:** `https://demo.dxfeed.com/webservice/rest` (demo, delayed data)

#### Tags

- Market Data
- REST
- Server-Sent Events
- Quotes
- Trades

#### Properties

- [Documentation](https://kb.dxfeed.com/en/market-data-api/data-access-solutions/rest.html)
- [API Reference](https://demo.dxfeed.com/webservice/rest/help)
- [Sandbox](https://tools.dxfeed.com/webservice/rest-demo.jsp)

### dxFeed dxLink WebSocket API

dxLink is dxFeed's WebSocket protocol for real-time market data streaming with multiplexed virtual channels, authorization, and FEED/DOM (order book) service channels. The protocol is publicly specified as an AsyncAPI 2.4 document in the dxFeed/dxLink GitHub repository, with a live demo server and an interactive debug console; client SDKs exist for JavaScript, Java, .NET, C++, and Swift.

- **Human URL:** [https://kb.dxfeed.com/en/market-data-api/data-access-solutions/websocket.html](https://kb.dxfeed.com/en/market-data-api/data-access-solutions/websocket.html)
- **Base URL:** `wss://demo.dxfeed.com/dxlink-ws` (demo)

#### Tags

- WebSocket
- Streaming
- Real-Time
- Market Data

#### Properties

- [Documentation](https://kb.dxfeed.com/en/market-data-api/data-access-solutions/websocket.html)
- [AsyncAPI](openapi/dxfeed-dxlink-asyncapi.yml) — harvested verbatim from [dxFeed/dxLink](https://github.com/dxFeed/dxLink) `dxlink-specification/asyncapi.yml`
- [Sandbox / Debug Console](https://demo.dxfeed.com/market-data/dxlink-ws/debug/)
- [GitHub Repository](https://github.com/dxFeed/dxLink)

### dxFeed Instrument Profile (IPF) Web Service

Reference-data web service for requesting instrument profiles in dxFeed's Instrument Profile Format (IPF), including live incremental updates, covering the 3.5M instruments in the dxFeed symbology universe. The documented host requires customer credentials (HTTP 401 without entitlements).

- **Human URL:** [https://kb.dxfeed.com/en/data-model/reference-data/ipf-webservice.html](https://kb.dxfeed.com/en/data-model/reference-data/ipf-webservice.html)
- **Base URL:** `https://tools.dxfeed.com/ipf` (credential-gated)

#### Tags

- Reference Data
- Instruments
- Symbology

#### Properties

- [Documentation](https://kb.dxfeed.com/en/data-model/reference-data/ipf-webservice.html)

### dxFeed Fundamentals API

Fundamental equity data sourced from Morningstar and Borsa Istanbul for ~45,000 companies — financial statements, valuations, dividends, earnings ratios, insider trading, corporate calendars — delivered as JSON from regional hosts. A Swagger UI exists at tools.dxfeed.com/fs/swagger-ui.html but both it and the underlying spec are credential-gated (HTTP 401), so no spec could be harvested.

- **Human URL:** [https://kb.dxfeed.com/en/data/fundamentals.html](https://kb.dxfeed.com/en/data/fundamentals.html)
- **Base URL:** `https://tools.dxfeed.com/morningstar` (credential-gated; also /morningstar-eur, /morningstar-asp)

#### Tags

- Fundamentals
- Equities
- Morningstar

#### Properties

- [Documentation](https://kb.dxfeed.com/en/data/fundamentals.html)

### dxFeed FIX API

Industry-standard FIX protocol access to dxFeed market data for trading systems. Session endpoints and credentials are provisioned during onboarding; no public FIX gateway host is documented.

- **Human URL:** [https://kb.dxfeed.com/en/market-data-api/data-access-solutions/fix.html](https://kb.dxfeed.com/en/market-data-api/data-access-solutions/fix.html)

#### Tags

- FIX
- Market Data
- Trading Systems

#### Properties

- [Documentation](https://kb.dxfeed.com/en/market-data-api/data-access-solutions/fix.html)

### dxFeed Historical Data Services

Historical data access covering candle/aggregated data and raw tick data extraction (dxFeed stores up to 10TB of raw data per day). The knowledge base documents how to request tick data and read extracted files; access hosts and credentials are entitlement-managed and issued by sales.

- **Human URL:** [https://kb.dxfeed.com/en/data-services/historical-services.html](https://kb.dxfeed.com/en/data-services/historical-services.html)

#### Tags

- Historical Data
- Tick Data
- Candles

#### Properties

- [Documentation](https://kb.dxfeed.com/en/data-services/historical-services.html)

## Common Properties

- [Website](https://dxfeed.com/)
- [Portal](https://kb.dxfeed.com/en/getting-started.html)
- [Documentation](https://kb.dxfeed.com/en/index-en.html)
- [GitHub Organization](https://github.com/dxFeed)
- [LinkedIn](https://www.linkedin.com/company/dxfeed)
- [Blog](https://dxfeed.com/dxfeed-news/)
- [Sign Up (data store)](https://get.dxfeed.com/)
- [Support](https://dxfeed.com/support/)
- [Terms of Service](https://dxfeed.com/terms-of-use/)
- [Privacy Policy](https://dxfeed.com/privacy-policy/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
