# Shopify Store Analyzer

![Shopify Store Analyzer](https://raw.githubusercontent.com/smoldesk/apify-scrapers/main/assets/shopify/banner.webp)

Check which apps, theme and tools any Shopify store uses, find its contact details and export its products. Paste domains, no login. Runs on [Apify](https://apify.com/smoldesk/shopify-store-analyzer).

## What you get

- **Is it Shopify?** Paste any list of domains. Other sites come back marked non-Shopify and are free.
- **Apps and tools**: installed app embeds with Shopify App Store links, plus pixels and tools such as Klaviyo, Meta Pixel and Google Tag Manager.
- **Theme**: name, base theme (for example Dawn) and version.
- **Contacts**: emails, phone numbers and social links from the store, contact and about pages.
- **Store profile**: city, country, currency, locale, product and collection counts, price range, top vendors, product types and shipping countries.
- **Activity**: newest product date and last product update.
- **Product export** (optional): the catalog, plus a CSV ready for Shopify import.

## Run it

Open the [Shopify Store Analyzer on Apify](https://apify.com/smoldesk/shopify-store-analyzer), fill in the form and click Start. Or call it from code with your [Apify token](https://console.apify.com/settings/integrations):

```bash
curl -X POST "https://api.apify.com/v2/acts/smoldesk~shopify-store-analyzer/run-sync-get-dataset-items?token=YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "storeUrls": ["deathwishcoffee.com", "allbirds.com"],
    "scanContactPages": true,
    "includeProducts": true,
    "maxProductsPerStore": 250
  }'
```

## Sample output

```json
{
  "name": "Death Wish Coffee",
  "url": "https://www.deathwishcoffee.com",
  "myshopifyDomain": "deathwishcoffee.myshopify.com",
  "country": "US",
  "currency": "USD",
  "productsCount": 145,
  "theme": {"schemaName": "Dawn", "schemaVersion": "10.0.0"},
  "apps": [
    {"handle": "klaviyo-email-marketing-sms", "url": "https://apps.shopify.com/klaviyo-email-marketing-sms"}
  ],
  "technologies": ["Google Tag Manager", "Gorgias"],
  "emails": ["hey@deathwishcoffee.com"],
  "priceMin": 5.0,
  "priceMax": 119.99,
  "priceAvg": 40.2
}
```

Export as JSON, CSV or Excel, or pipe it into Google Sheets, Make, Zapier or n8n.

## Pricing

Pay per result. No monthly fee.

| Result | Per 1,000 |
|---|---|
| Shopify store analyzed | $5 |
| Product exported | $0.50 |
| Non-Shopify URL | Free |

## Limits

- Public storefront data only. No orders, sales or customer data, and no password-protected stores.
- App detection sees apps that load on the storefront. Back-office apps are invisible.
- Some stores hide `products.json`. You still get the store analysis.

## FAQ

**How do I check if a website uses Shopify?**
Paste the domains into `storeUrls`. Shopify stores get the full analysis and the rest are marked non-Shopify at no charge.

**How do I find which apps a Shopify store uses?**
Read the `apps` field for app embeds and `technologies` for pixels and tools.

**How do I find a Shopify store's contact email?**
Keep `scanContactPages` on. Emails, phones and social links are collected from the store, contact and about pages.

**Do I need a Shopify API key or store access?**
No. Only public storefront data is used.

**Can I export a store's products to my own Shopify store?**
Turn on `exportShopifyCsv` to build a Shopify import CSV. Check you have the rights to the images and descriptions.

## More scrapers

Shopify Store Analyzer is one of 20 no-login scrapers by Smoldesk Studios. See the full list: [smoldesk/apify-scrapers](https://github.com/smoldesk/apify-scrapers).
