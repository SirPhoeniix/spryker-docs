---
title: URL Schema
originalLink: https://documentation.spryker.com/2021080/docs/db-schema-url
originalArticleId: 570cbdcd-b3a2-484f-baac-931db5e213ad
redirect_from:
  - /2021080/docs/db-schema-url
  - /2021080/docs/en/db-schema-url
  - /docs/db-schema-url
  - /docs/en/db-schema-url
---

## URL

### URLs

Yves knows two types of URLs (see `YvesBootstrap`->`registerRouters()`).

1. URLs that are defined in the database (e.g. for Product Detail, CMS or Category Pages).
2. URLs that are defined in the code (e.g. for Cart and Checkout).
![URL](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Database+Schema+Guide/URL+Schema/url.png){height="" width=""}

Structure:

* All URLs which are in the first category are stored in `spy_url`.
* Each URL is assigned to one Locale which means that there are multiple URLs per linked Resource (e.g. a Product Detail Page has one translated URL per Locale).

### URL Resources

{% info_block infoBox %}
URLs are related to Resources. A Resource can be something like a Category- or a Product Detail Page. Each Resource has one URL per Locale.
{% endinfo_block %}
![URL resources](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Database+Schema+Guide/URL+Schema/url-resources.png){height="" width=""}

**Structure**:

* Several Resources are related to URLs
* The `spy_url` table holds all the foreign keys but there is a constraint that only one of the foreign keys is possible (in other words: One URL cannot be related to more than one resource).
