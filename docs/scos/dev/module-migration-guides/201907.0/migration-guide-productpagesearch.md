---
title: Migration Guide - ProductPageSearch
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-product-page-search
originalArticleId: 6bcb312f-8566-4d3d-9ac4-12730212c562
redirect_from:
  - /v3/docs/mg-product-page-search
  - /v3/docs/en/mg-product-page-search
---

## Upgrading from Version 2.* to 3.*
`ProductPageSearch` 3.0.0 got separate search index for Concrete Products. It includes database table and ElasticSearch index.
To perform the migration, follow the steps:

1. Run the database migration:
`vendor/bin/console propel:install`
2. Generate transfers:
`vendor/bin/console transfer:generate`
3. Install search:
`vendor/bin/console search:setup`
4. Sync concrete products data with ElasticSearch:
`vendor/bin/console data:import:product-concrete`
or
`vendor/bin/console event:trigger -r product_concrete`

_Estimated migration time: ~2h_

<!-- Last review date: Mar 13, 2019 by Stanislav Matveyev, Oksana Karasyova -->
