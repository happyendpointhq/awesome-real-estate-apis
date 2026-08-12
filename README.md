# Awesome Real Estate APIs [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of APIs and data sources for property listings, transactions,
valuations, and market data, organised by country.

Includes official portal APIs, government open data, commercial providers, and
scraping platforms. Free sources are marked, and access restrictions are stated
plainly, because most lists on this subject quietly omit that the API they are
recommending requires a brokerage licence.

---

## The thing nobody tells you first

In almost every market, the authoritative property data exists and is gated.

| Market | Authoritative source | Who can actually get it |
|---|---|---|
| US | MLS via RESO Web API | Licensed brokers and agents, or approved vendors. There is no tier an unlicensed developer can buy |
| US | Zillow public API | Closed to new developers since 2021 |
| US | Bridge Listing Output | Invite only |
| UK | HM Land Registry Price Paid | **Genuinely open.** Open Government Licence, free, monthly updates |
| UAE | Dubai Land Department | Open data on Dubai Pulse; the DLD API Gateway expects a registered business entity |
| Spain | Idealista official API | Vetted business partners only, not open to individual developers |

That gap between "the data exists" and "you can have it" is why the third-party
market in this list exists at all. It is worth understanding before you pick a
provider, because it explains the price differences.

---

## Contents

- [How to choose](#how-to-choose)
- [Government and open data](#government-and-open-data) (free)
- [United States](#united-states)
- [United Kingdom and Ireland](#united-kingdom-and-ireland)
- [Europe](#europe)
- [Middle East](#middle-east)
- [Asia Pacific](#asia-pacific)
- [Other markets](#other-markets)
- [Valuation and analytics](#valuation-and-analytics)
- [Web scraping platforms](#web-scraping-platforms)
- [Adjacent data](#adjacent-data)
- [Datasets](#datasets)
- [Libraries and tools](#libraries-and-tools)
- [Legal and ethical notes](#legal-and-ethical-notes)
- [Contributing](#contributing)

---

## How to choose

Work down this list and stop at the first one that fits.

**1. Is there open government data for your market?** In the UK, the US at
county level, and increasingly in the UAE, there is. It is free, authoritative,
and you should exhaust it before paying anyone. It is usually bulk files rather
than a live API, and it covers completed transactions rather than current
listings.

**2. Are you licensed, or working with someone who is?** If so, go direct: RESO
Web API in the US, or the official portal APIs in Europe. Best data, lowest cost,
most friction to set up.

**3. Do you need current listings rather than sold history?** Listings are not in
government data. You need a portal, an aggregator, or an unofficial API.

**4. Do you need one market or many?** Single-market projects are usually better
served by a country-specific provider. Multi-market projects favour aggregators
or a scraping platform, at higher cost per record.

**5. Live queries or a bulk snapshot?** Dashboards and search need an API.
Analysis, modelling, and backtesting usually want a file. Many providers sell
both and the file is far cheaper per record.

---

## Government and open data

Free, authoritative, and underused. Mostly transactions rather than listings.

### United States

- [FHFA House Price Index](https://www.fhfa.gov/data/hpi) - Official US house price indices, national through to ZIP-code level. Free bulk files.
- [Census Bureau Building Permits Survey](https://www.census.gov/construction/bps/) - New residential construction permits by geography. Free, and a useful leading indicator of supply.
- [HUD USER datasets](https://www.huduser.gov/portal/pdrdatas_landing.html) - Fair market rents, income limits, and assisted housing data. Free.
- [FEMA National Flood Hazard Layer](https://www.fema.gov/flood-maps/national-flood-hazard-layer) - Flood zone designations, which materially affect valuation and insurance. Free API.
- County assessor and recorder offices - Parcel, assessment, and deed data. Free but fragmented across roughly 3,000 counties with no common format. This fragmentation is the entire business model of the US property data industry.

### United Kingdom

- [HM Land Registry Price Paid Data](https://landregistry.data.gov.uk/app/ppd/) - Every registered residential sale in England and Wales since 1995. Open Government Licence, updated monthly. Includes price, date, property type, tenure, and new-build flag. **The single best free property dataset anywhere.**
- [Use land and property data](https://use-land-property-data.service.gov.uk/) - HM Land Registry's wider data service. Most datasets free; some need an account and a signed licence.
- [Energy Performance Certificates](https://epc.opendatacommunities.org/) - EPC register for England and Wales. Free, and gives you floor area and energy rating keyed to address.
- [planning.data.gov.uk](https://www.planning.data.gov.uk/) - Planning and land designation data.
- [Registers of Scotland](https://www.ros.gov.uk/data-and-statistics) - Scotland is a separate registry from England and Wales. Easy to miss.

### UAE

- [Dubai Pulse](https://www.dubaipulse.gov.ae/data/dld-transactions/dld_transactions-open) - Dubai Land Department transaction history as open data. Regularly updated CSV, with REST API access available. The authoritative record of what Dubai property actually sold for.
- [Dubai Land Department open data](https://dubailand.gov.ae/en/open-data/real-estate-data/) - DLD's own portal. The [API Gateway](https://dubailand.gov.ae/en/eservices/api-gateway/) exists but expects a registered business entity, so it is not a practical route for an individual developer.

### Europe

- [Sede Electrónica del Catastro](https://www.sedecatastro.gob.es/) - Spanish cadastre. Free web services for parcel and building data, though the documentation is Spanish-only and the SOAP interfaces show their age.
- [Kadaster](https://www.kadaster.nl/zakelijk/producten) - Dutch land registry. Some open datasets, most products paid.
- [INSEE and DVF](https://www.data.gouv.fr/fr/datasets/demandes-de-valeurs-foncieres/) - French property transaction values, published as open data. The equivalent of the UK's Price Paid.
- [European Data Portal](https://data.europa.eu/) - Aggregates open data across member states. Worth searching before assuming a country has nothing.

### Australia and New Zealand

- [data.gov.au property datasets](https://data.gov.au/) - State-level transaction and valuation data, varying in quality by state.
- [LINZ Data Service](https://data.linz.govt.nz/) - New Zealand land information, free with registration.

---

## United States

The most fragmented market in the world, and the most expensive to serve.

### Official and licensed

- [RESO Web API](https://www.reso.org/reso-web-api/) - The standard MLS data interface. Requires broker or agent membership, or an approved vendor agreement. If you qualify, this is the best data available.
- [Bridge Interactive](https://www.zillowgroup.com/developers/api/mls-broker-data/mls-listings/) - Zillow Group's MLS distribution platform, normalised to the RESO data dictionary. Invite only.
- [MLS Grid](https://www.mlsgrid.com/) - Normalised RESO feeds across participating MLSs. Still requires MLS authorisation, but consolidates the paperwork.
- [Realtors Property Resource](https://www.narrpr.com/) - National property database. NAR members only.

### Commercial providers

- [ATTOM Data](https://www.attomdata.com/) - Property, deed, mortgage, foreclosure, and neighbourhood data across US properties. Enterprise pricing, long-established.
- [CoreLogic](https://www.corelogic.com/) - Property records, AVMs, and risk data. Enterprise.
- [Estated](https://estated.com/) - Property records with a self-serve API and a free tier. Friendlier entry point than the enterprise providers.
- [Rentcast](https://www.rentcast.io/api) - Rental estimates, listings, and property records. Self-serve with a free tier.
- [Realtor.com API (Happy Endpoint)](https://happyendpoint.com/library) - Unofficial API over Realtor.com listing data. Self-serve via RapidAPI.
- [Auction.com API (Happy Endpoint)](https://happyendpoint.com/library/auction-com-api) - Foreclosure and auction listings, a segment most providers skip.

---

## United Kingdom and Ireland

- [HM Land Registry Price Paid](https://landregistry.data.gov.uk/app/ppd/) - Free, official, sold prices. Start here.
- [PropertyData](https://propertydata.co.uk/) - UK market analytics API covering prices, rents, yields, and planning. Self-serve.
- [Homedata](https://homedata.co.uk/) - Aggregates HM Land Registry, EPC, flood risk, council tax bands, and UPRN into one normalised API. Free tier available. A good example of the "stitch together the open data for you" model.
- [Rightmove API (Happy Endpoint)](https://happyendpoint.com/library/rightmove-uk) - Unofficial API over Rightmove listings. Rightmove has no public API of its own.
- [Gumtree API (Happy Endpoint)](https://happyendpoint.com/library/gumtree-api) - Classifieds including property, useful for the private-landlord segment that misses the big portals.
- [Zoopla](https://developers.zoopla.co.uk/) - A developer programme exists on paper, but it has been effectively unmaintained for years, with reports of keys silently ceasing to work. Listed for completeness. Verify current status before planning around it.

---

## Europe

### Spain

- [Idealista API](https://developers.idealista.com/access-request) - Official, and the best data for Spain if you can get in. Restricted to vetted business partners; individual developers are not accepted.
- [Idealista API (Happy Endpoint)](https://happyendpoint.com/library/idealista-api) - Unofficial, self-serve alternative for developers who cannot get official access.
- [Fotocasa API (Happy Endpoint)](https://happyendpoint.com/library/fotocasa-api) - Spain's second major portal. Inventory only partly overlaps Idealista, so serious Spanish coverage means both.
- [Catastro web services](https://www.sedecatastro.gob.es/) - Free official cadastre data for parcels and buildings.

### Turkey

- [Emlakjet API (Happy Endpoint)](https://happyendpoint.com/library/emlakjet-api) - Turkish property listings.
- [Hepsiemlak API (Happy Endpoint)](https://happyendpoint.com/library/hepsiemlak-api) - The other major Turkish portal.

### Elsewhere

- [Njuskalo API (Happy Endpoint)](https://happyendpoint.com/library/njuskalo-api) - Croatia's dominant classifieds site, including property.
- [ImmoScout24](https://api.immobilienscout24.de/) - Germany's largest portal. Partner API, restricted access.
- [Pararius and Funda (Netherlands)](https://www.funda.nl/) - No public APIs. Dutch coverage generally means scraping or a commercial aggregator.

---

## Middle East

The UAE is unusually well served, because both major portals have third-party
API coverage and the government publishes transactions openly.

- [Dubai Pulse DLD transactions](https://www.dubaipulse.gov.ae/data/dld-transactions/dld_transactions-open) - Free, official, what property actually sold for.
- [Bayut API (Happy Endpoint)](https://happyendpoint.com/library/bayut-api) - Listings, agents, agencies, off-plan projects, and transaction history from the UAE's largest portal.
- [PropertyFinder API (Happy Endpoint)](https://happyendpoint.com/library/propertyfinder-api) - The other dominant UAE portal, including commercial property and broker data.
- [Aqar API (Happy Endpoint)](https://happyendpoint.com/library/aqar-api) - Saudi Arabian property listings.
- [Yad2 API (Happy Endpoint)](https://happyendpoint.com/library/yad2-api) - Israel's dominant classifieds platform.
- [Bayut and Dubizzle official](https://www.bayut.com/) - No public developer API.

A note on the UAE specifically: listings and DLD transactions answer different
questions. Listings tell you what sellers are asking today. DLD tells you what
buyers actually paid. Off-plan analysis in particular needs both, since asking
prices on under-construction stock can diverge a long way from recorded sales.

---

## Asia Pacific

- [99co API (Happy Endpoint)](https://happyendpoint.com/library/99co-api) - Singapore property listings.
- [Suumo API (Happy Endpoint)](https://happyendpoint.com/library/suumo-api) - Japan's largest property portal.
- [URA Data Service](https://eservice.ura.gov.sg/maps/api/) - Singapore Urban Redevelopment Authority. Free official API covering private residential transactions. Register for an access key at the [registration page](https://eservice.ura.gov.sg/maps/api/reg.html). Excellent and underused.
- [HDB resale prices](https://data.gov.sg/collections/189/view) - Singapore public housing resale transactions, free and complete. Singapore is arguably the best-served market in the world for open property data.
- [Domain API](https://developer.domain.com.au/) - Australian listings. Self-serve with a free tier, which is rare among portal APIs.
- [CoreLogic Australia](https://www.corelogic.com.au/) - Australian valuations and property records. Enterprise.

---

## Other markets

- [UAE Real Estate API (Happy Endpoint)](https://happyendpoint.com/library/uae-realestate-api) - Cross-portal UAE aggregate.
- [Nestoria API](https://www.nestoria.co.uk/help/api) - One of the longest-running free portal APIs, historically covering several countries. Country coverage has narrowed over the years and current status is hard to confirm, so verify before building on it.

---

## Valuation and analytics

- [HouseCanary](https://www.housecanary.com/) - US AVMs and forecasts. Enterprise.
- [Quantarium](https://quantarium.com/) - US AVM and property data.
- [PropertyData](https://propertydata.co.uk/) - UK yields, rents, and area analytics.
- [Rentcast](https://www.rentcast.io/api) - US rent estimates with a free tier.
- [Dubai rental yield calculator](https://github.com/happyendpointhq/dubai-rental-yield-calculator) - Open source, computes gross and net yields from live listings.

An honest caveat on AVMs: accuracy varies enormously by market and property
type. Every vendor quotes a median error that flatters them. Test against known
sales in your specific geography before relying on one.

---

## Web scraping platforms

The DIY route. Higher effort, more legal exposure, but works anywhere no API
exists. Pricing below reflects publicly listed rates as of August 2026 and
changes often.

- [Bright Data](https://brightdata.com/) - Largest proxy network with hundreds of pre-built scrapers. Residential proxies around $10.50/GB. Best for heavily protected targets at scale.
- [Apify](https://apify.com/) - Marketplace of community and first-party scrapers, including many property portals. Per-compute-unit or per-result pricing depending on the actor.
- [Oxylabs](https://oxylabs.io/) - Residential proxies from around $8/GB, Web Scraper API from around $49/month.
- [ScraperAPI](https://www.scraperapi.com/) - Simple proxy and rendering API, from around $49/month for 100k credits. Cheapest for low volume on a single target.
- [Zyte](https://www.zyte.com/) - Pay-as-you-go with difficulty tiers. Good rates on easy sites, expensive on hard ones.

When scraping is the wrong answer: if a maintained API already covers your
target, it is almost always cheaper once you count engineering time. Portals
change markup frequently, and a scraper is a permanent maintenance commitment,
not a one-off build.

---

## Adjacent data

Often more useful than more listing data.

- [OpenStreetMap Overpass API](https://wiki.openstreetmap.org/wiki/Overpass_API) - Free amenity, transport, and POI data. Proximity to schools and transport drives a lot of price variance.
- [Google Places API](https://developers.google.com/maps/documentation/places/web-service) - Commercial POI and neighbourhood data.
- [Ordnance Survey Data Hub](https://osdatahub.os.uk/) - UK mapping and UPRN. Free tier available.
- [WalkScore API](https://www.walkscore.com/professional/api.php) - Walkability, transit, and bike scores.
- [OpenWeather](https://openweathermap.org/api) - Climate data, increasingly relevant to valuation as insurance repricing spreads.
- [FRED](https://fred.stlouisfed.org/docs/api/fred/) - US interest rates and economic series. Free. Mortgage rates drive transaction volume more than any property-level variable.

---

## Datasets

Bulk files, for analysis rather than live queries.

- [HM Land Registry Price Paid](https://landregistry.data.gov.uk/app/ppd/) - Free, complete, England and Wales since 1995.
- [Dubai Pulse DLD transactions](https://www.dubaipulse.gov.ae/data/dld-transactions/dld_transactions-open) - Free, complete Dubai transaction history.
- [Kaggle real estate datasets](https://www.kaggle.com/datasets?search=real+estate) - Mixed quality, often stale, but useful for prototyping and teaching.
- [Zillow Research Data](https://www.zillow.com/research/data/) - Free aggregate US indices such as ZHVI and ZORI. Not listing-level, but genuinely useful and genuinely free.
- [Happy Endpoint datasets](https://happyendpoint.com/datasets) - Bulk snapshots for the covered portals, with free samples that share the paid schema.

---

## Libraries and tools

- [happyendpoint-python](https://github.com/happyendpointhq/happyendpoint-python) - Python client for property, retail, and travel APIs.
- [happyendpoint-js](https://github.com/happyendpointhq/happyendpoint-js) - TypeScript equivalent.
- [happyendpoint-mcp](https://github.com/happyendpointhq/happyendpoint-mcp) - MCP server, so Claude, Cursor, and similar can query property data directly.
- [idealista-api](https://github.com/yagueto/idealista-api) - Community Python client for the official Idealista API.
- [dubai-property-price-tracker](https://github.com/happyendpointhq/dubai-property-price-tracker) - Open source listing monitor with price-drop alerts.

---

## Legal and ethical notes

Not legal advice, but worth stating because most lists on this subject do not.

**Terms of service.** Most property portals prohibit automated access in their
terms. Using an unofficial API does not transfer that risk to the provider; it
changes who does the collecting, not whether the portal permits it. Read the
terms for your jurisdiction and use case.

**Personal data.** Agent names, phone numbers, and emails appear throughout this
data. Under GDPR, UK GDPR, and similar regimes, that is personal data with
obligations attached, whatever the source. Storing and processing agent contact
details needs a lawful basis.

**Copyright in listings.** Listing text and photographs are typically the
copyright of the agent or portal. Facts about a property, such as price and size,
generally are not. Republishing descriptions and images is a different risk to
analysing prices.

**Rate limits and courtesy.** Even where collection is permitted, hammering an
endpoint is not. Every reputable provider on this list rate limits; respect it.

---

## Contributing

Additions welcome, including competitors to anything already listed. The value of
this list is that it is honest about what each option actually gives you.

Please:

- Say plainly if access is restricted, invite-only, or requires a licence
- Mark free and open sources as free
- Skip marketing language. "Comprehensive coverage" tells a reader nothing
- Prefer a link to documentation over a link to a pricing page
- One entry per line, in the existing format

Open an issue or a pull request.

---

## Maintained by

This list is maintained by [Happy Endpoint](https://happyendpoint.com), which
builds real-time data APIs for property portals and marketplaces. Our APIs appear
in it alongside competitors, government sources, and free alternatives, several
of which are better choices for particular use cases. A list that only
recommended its maintainer would not be worth reading.

- Catalogue: [happyendpoint.com/library](https://happyendpoint.com/library)
- Datasets: [happyendpoint.com/datasets](https://happyendpoint.com/datasets)
- Contact: happyendpointhq@gmail.com

## Licence

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and
related rights to this work.
