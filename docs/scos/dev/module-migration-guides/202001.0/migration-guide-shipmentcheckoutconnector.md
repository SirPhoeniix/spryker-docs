---
title: Migration Guide - ShipmentCheckoutConnector
description: Use the guide to learn how to update the ShipmentCheckoutConnector module to a newer version.
last_updated: Nov 27, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v4/docs/mg-shipment-checkout-connector
originalArticleId: 9b97c4a6-3282-4b48-ab38-b7e8c903c99c
redirect_from:
  - /v4/docs/mg-shipment-checkout-connector
  - /v4/docs/en/mg-shipment-checkout-connector
---

## Upgrading from Version 1.0.* to Version 2.0.0

In this new version of the **ShipmentCheckoutConnector** module, we have added support of split delivery. You can find more details about the changes on the ShipmentCheckoutConnector module release page.

{% info_block errorBox %}
This release is a part of the Split delivery concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Split Delivery Migration Concept](/docs/scos/dev/migration-concepts/split-delivery-migration-concept.html).
{% endinfo_block %}

**To upgrade to the new version of the module, do the following:**

1. Upgrade the **ShipmentCheckoutConnector** module to the new version:

```bash
composer require spryker/shipment-сheckout-сonnector: "^2.0.0" --update-with-dependencies
```
2. Generate the transfer objects:

```bash
console transfer:generate
```

*Estimated migration time: 5 min*
