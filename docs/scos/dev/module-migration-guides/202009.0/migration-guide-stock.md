---
title: Migration Guide - Stock
description: Use the guide to migrate to a new version of the Stock module.
originalLink: https://documentation.spryker.com/v6/docs/mg-stock
originalArticleId: 6a873842-5ec7-4935-aeec-39467a24e27c
redirect_from:
  - /v6/docs/mg-stock
  - /v6/docs/en/mg-stock
---

## Upgrading from Version 7.* to Version 8.0.0

In this new version of the **Stock** module, we have added support of decimal stock. You can find more details about the changes on the Stock module release page.

{% info_block errorBox %}
This release is a part of the **Decimal Stock** concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Decimal Stock Migration Concept](/docs/scos/dev/migration-concepts/decimal-stock-migration-concept.html
{% endinfo_block %}.)

**To upgrade to the new version of the module, do the following:**

1. Upgrade the **Stock** module to the new version:

```bash
composer require spryker/stock: "^8.0.0" --update-with-dependencies
```
2. Update the database entity schema for each store in the system:

```bash
APPLICATION_STORE=DE console propel:schema:copy
APPLICATION_STORE=US console propel:schema:copy
...
```
3. Run the database migration:

```bash
console propel:install
console transfer:generate
```
4. Resolve deprecations:

| Deprecated code | Replacement |
| --- | --- |
| `Spryker\Zed\Stock\StockConfig::getStoreToWarehouseMapping()` | Removed without replacement. |

*Estimated migration time: 5 min*
***
## Upgrading from Version 5.* to Version 7.0.0
{% info_block infoBox %}
To dismantle the Horizontal Barrier and enable partial module updates on projects, a Technical Release took place. Public API of source and target major versions are equal. No migration efforts are required. Please [contact us](https://support.spryker.com/hc/en-us
{% endinfo_block %} if you have any questions.)