---
title: Migration Guide - PriceProductSchedule
description: Use the guide to update the PriceProductSchedule module to a newer version.
last_updated: Nov 27, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v4/docs/mg-price-product-schedule
originalArticleId: 1257a624-0eaf-4813-9493-651fbc758f66
redirect_from:
  - /v4/docs/mg-price-product-schedule
  - /v4/docs/en/mg-price-product-schedule
---

## Upgrading from Version 1.* to Version 2.0.0

1. Upgrade the **PriceProductSchedule** module to version 2.0.0:

```bash
composer require spryker/price-product-schedule: "^2.0.0" --update-with-dependencies
```

2. Generate transfers:

```bash
console transfer:generate
```

*Estimated migration time: 5 minutes*
