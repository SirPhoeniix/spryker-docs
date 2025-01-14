---
title: Migration Guide - ProductPageSearch
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v2/docs/mg-product-page-search
originalArticleId: bf376f7c-f0f3-4f8b-bd1c-9d654378226f
redirect_from:
  - /v2/docs/mg-product-page-search
  - /v2/docs/en/mg-product-page-search
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
