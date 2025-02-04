---
title: Migration Guide - CheckoutRestApi
last_updated: Sep 14, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/mg-checkoutrestapi
originalArticleId: 666a5d96-4603-4f38-bdb3-6b6d5d326de3
redirect_from:
  - /v5/docs/mg-checkoutrestapi
  - /v5/docs/en/mg-checkoutrestapi
related:
  - title: Migration Guide - Payment
    link: docs/scos/dev/module-migration-guides/page.version/migration-guide-payment.html
---

## Upgrading from Version 2.* to Version 3.0.0

Version 3 of the **CheckoutRestApi** module adds the **Payment Method per Store** functionality.

**To upgrade to the new version of the module, do the following:**

1. Upgrade the `CheckoutRestApi` module to the new version:

```bash
composer require spryker/checkout-rest-api:"^2.0.0" --update-with-dependencies
```
2. Prepare a database entity schema for **each store** in the system:

```bash
APPLICATION_STORE=DE console propel:schema:copy
APPLICATION_STORE=US console propel:schema:copy
```
3. Run the database migration:

```bash
console propel:install
console transfer:generate
```

*Estimated migration time: 5 min*
***
## Upgrading from Version 1.* to Version 2.0.0

In this new version of the **CheckoutRestApi** module, we have added support of split delivery. You can find more details about the changes on the [CheckoutRestApi module](https://github.com/spryker/checkout-rest-api/releases) release page.

{% info_block errorBox %}
This release is a part of the **Split delivery** concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Split Delivery Migration Concept](/docs/scos/dev/migration-concepts/split-delivery-migration-concept.html).
{% endinfo_block %}

**To upgrade to the new version of the module, do the following:**

1. Upgrade the **CheckoutRestApi** module to the new version:

```bash
composer require spryker/checkout-rest-api: "^2.0.0" --update-with-dependencies
```
2. Generate the transfer objects:

```bash
console transfer:generate
```

*Estimated migration time: 5 min*
