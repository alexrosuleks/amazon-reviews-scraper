# Amazon Reviews Scraper: Amazon Scraper API for Python & Node.js (2026)

Scrape Amazon product reviews by ASIN or URL: rating, title, text, date, verified purchase and helpful votes. No login needed. Export to JSON, CSV or Excel.

**[▶ Try the Amazon Reviews Scraper free on Scrapely](https://scrape.ly/store/shelfbright/amazon-reviews-scraper)** · [Compare Scrapely vs other scraping tools](https://scrape.ly/compare)

This repository shows how to scrape Amazon data with the [Amazon Reviews Scraper](https://scrape.ly/store/shelfbright/amazon-reviews-scraper) using the official
**Scrapely SDKs for JavaScript and Python**. You pass the input, Scrapely runs the amazon scraper in the cloud
(proxies, retries, browser and scaling included) and returns clean, structured data as JSON, CSV or Excel.
No scraper code to maintain and no blocked requests to debug.

## Why use this Amazon scraper

- **No-code or API:** run it from the [Scrapely Store](https://scrape.ly/store/shelfbright/amazon-reviews-scraper) or from your code with the SDK.
- **Structured amazon data:** ready-to-use fields instead of raw HTML.
- **Pay per result:** $5.10 per 1,000 review results, no monthly subscription required.
- **Maintained and monitored:** scrapers are tested around the clock and fixed fast when Amazon changes.
- **Integrations:** n8n, Make, Zapier, LangChain, LlamaIndex, MCP (Claude, Cursor) and webhooks.

## What Amazon data can you extract?

Scrape Amazon product reviews by ASIN or URL: rating, title, text, date, verified purchase and helpful votes. No login needed. Export to JSON, CSV or Excel.

| Output field |
|---|
| `productAsin` |
| `ratingScore` |
| `reviewTitle` |
| `reviewDescription` |
| `date` |
| `country` |
| `isVerified` |
| `variant` |
| `reviewUrl` |

## Quick start

1. [Sign up for Scrapely](https://scrape.ly) (free plan available) and copy your API token from
   **Settings → API & Integrations**.
2. Clone this repo and set your token:

```bash
export SCRAPELY_TOKEN=your_token
```

### Node.js (JavaScript SDK)

```bash
npm install
node example.js
```

```js
const { ScrapelyClient } = require('scrapely-client');
const client = new ScrapelyClient({ token: process.env.SCRAPELY_TOKEN });

const run = await client.actor('shelfbright/amazon-reviews-scraper').call({"productUrls": [{"url": "https://www.amazon.com/dp/B0CWXNS552"}], "maxReviews": 10, "sort": "helpful", "filterByRatings": ["allStars"], "includeGdprSensitive": false, "reviewsUseProductVariantFilter": false, "proxyConfiguration": {"useScrapelyProxy": true, "scrapelyProxyGroups": ["DATACENTER"]}});
const { items } = await client.dataset(run.defaultDatasetId).listItems();
```

### Python (Python SDK)

```bash
pip install -r requirements.txt
python example.py
```

```python
from scrapely_client import ScrapelyClient
client = ScrapelyClient(os.environ['SCRAPELY_TOKEN'])

run = client.actor('shelfbright/amazon-reviews-scraper').call(run_input={ "productUrls": [ { "url": "https://www.amazon.com/dp/B0CWXNS552" } ], "maxReviews": 10, "sort": "helpful", "filterByRatings": [ "allStars" ], "includeGdprSensitive": False, "reviewsUseProductVariantFilter": False, "proxyConfiguration": { "useScrapelyProxy": True, "scrapelyProxyGroups": [ "DATACENTER" ] } })
items = list(client.dataset(run.default_dataset_id).iterate_items())
```

### REST API / cURL

```bash
curl -X POST "https://api.scrape.ly/v2/acts/shelfbright~amazon-reviews-scraper/run-sync-get-dataset-items?token=$SCRAPELY_TOKEN" \
  -H "Content-Type: application/json" \
  -d @input.json
```

## Example input

```json
{
  "productUrls": [
    {
      "url": "https://www.amazon.com/dp/B0CWXNS552"
    }
  ],
  "maxReviews": 10,
  "sort": "helpful",
  "filterByRatings": [
    "allStars"
  ],
  "includeGdprSensitive": false,
  "reviewsUseProductVariantFilter": false,
  "proxyConfiguration": {
    "useScrapelyProxy": true,
    "scrapelyProxyGroups": [
      "DATACENTER"
    ]
  }
}
```

See every input option on the [Amazon Reviews Scraper page](https://scrape.ly/store/shelfbright/amazon-reviews-scraper).

## Pricing

**$5.10 per 1,000 review results.** Free plan available, no credit card needed to start. Check current pricing on the
[Store page](https://scrape.ly/store/shelfbright/amazon-reviews-scraper) and see how Scrapely compares with other tools on [scrape.ly/compare](https://scrape.ly/compare).

## FAQ

**How do I scrape Amazon with Python?** Install `scrapely-client-python`, set `SCRAPELY_TOKEN` and run
`example.py`. The scraper runs on Scrapely and you read the results from the dataset.

**How do I scrape Amazon with Node.js?** Install `scrapely-client`, set `SCRAPELY_TOKEN` and run `example.js`.

**Is there a amazon scraper API?** Yes. Call `POST https://api.scrape.ly/v2/acts/shelfbright~amazon-reviews-scraper/runs`
or use `run-sync-get-dataset-items` to get results in one request.

**Do I need proxies?** No. Proxies, retries and browsers are handled by Scrapely.

**Is scraping Amazon legal?** This scraper collects publicly available data. Check Amazon's terms and the
laws that apply to you, especially for personal data (GDPR, CCPA).

**Can I schedule it or get results by webhook?** Yes. Use Scrapely schedules and webhooks, or n8n, Make and Zapier.

## Related Amazon scrapers

- [Amazon Product Scraper](https://github.com/alexrosuleks/amazon-product-scraper): Scrape Amazon products by URL, ASIN or search: price, rating, reviews count, seller, images and specs. No login needed.…
- [Amazon Bestsellers Scraper](https://github.com/alexrosuleks/amazon-bestsellers-scraper): Scrape Amazon Best Sellers lists for any category and country: rank, title, ASIN, price, rating and reviews count. No…

## Looking for an alternative?

Scrapely is an alternative to Apify, Bright Data, ScraperAPI, Firecrawl, Octoparse, PhantomBuster, SerpApi,
Zyte and others. See the side-by-side pricing on [scrape.ly/compare](https://scrape.ly/compare).

---

**Keywords:** amazon reviews scraper, amazon scraper, amazon scraper api, amazon scraper python, amazon scraper node.js,
scrape amazon, amazon data extraction, amazon crawler, amazon api, export amazon data to csv, amazon-reviews-scraper

License: MIT. Example code only; the scraper runs on [Scrapely](https://scrape.ly/store/shelfbright/amazon-reviews-scraper).
