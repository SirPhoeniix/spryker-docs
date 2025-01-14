---
title: Migration Guide - ShipmentDiscountConnector
last_updated: Jul 29, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v1/docs/mg-shipment-discount-connector
originalArticleId: fbb3ba66-aecc-4fb4-8f5f-215a6b1c33fa
redirect_from:
  - /v1/docs/mg-shipment-discount-connector
  - /v1/docs/en/mg-shipment-discount-connector
---

## Upgrading from Version 3.0.* Version to 4.0.0

In this new version of the **ShipmentDiscountConnector** module, we have added support of split delivery. You can find more details about the changes on the [ShipmentDiscountConnector module release page](https://github.com/spryker/shipment-discount-connector/releases).

{% info_block errorBox %}
This release is a part of the **Split delivery** concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Split Delivery Migration Concept](/docs/scos/dev/migration-concepts/split-delivery-migration-concept.html)).
{% endinfo_block %}

**To upgrade to the new version of the module, do the following:**

1. Upgrade the `ShipmentDiscountConnector` module to the new version:

```bash
composer require spryker/shipment-discount-connector: "^4.0.0" --update-with-dependencies
```

2. Generate the transfer objects:

```bash
console transfer:generate
```

*Estimated migration time: 5 min*

## Upgrading from Version 1.* to Version 3.0.0

{% info_block infoBox %}
To dismantle the Horizontal Barrier and enable partial module updates on projects, a Technical Release took place. Public API of source and target major versions are equal. No migration efforts are required. Please [contact us](https://spryker.com/en/support/) if you have any questions.
{% endinfo_block %}

<!-- Last review date: Sep 18, 2019 by Denys Sokolov, Yuliia Boiko -->
