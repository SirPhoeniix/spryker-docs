---
title: Split delivery migration concept
description: The article provides instructions on how to install Split Delivery on all modules affected in bulk and then individually.
originalLink: https://documentation.spryker.com/v6/docs/split-delivery-concept
originalArticleId: e9badade-538d-41bf-82c6-6247226e030b
redirect_from:
  - /v6/docs/split-delivery-concept
  - /v6/docs/en/split-delivery-concept
---

## General Information
Split Delivery splits order items into different shipments according to a delivery address, a shipment method, and a delivery date. The feature also provides an ability to edit a shipment or create a new one for the existing order in the Back Office.

## Migration process
You can upgrade all affected modules by the feature in bulk.

**To update all the modules affected by feature in bulk, do the following:**

1. Run the following composer command, but make sure **to remove the modules that are irrelevant for your project from the command**:

```bash
composer update "spryker/*" "spryker-shop/*"
 composer require spryker/sales: "^11.0.0" spryker/shipment: "^7.0.0" spryker-shop/checkout-page: "^3.0.0" spryker-shop/customer-page: "^2.0.0" spryker/checkout-rest-api: "^2.0.0" spryker/manual-order-entry-gui:"^0.8.0" spryker/shipment-cart-connector:"^2.0.0" spryker/shipment-checkout-connector:"^2.0.0" spryker/shipment-discount-connector:"^4.0.0" spryker/orders-rest-api: "^4.0.0" --update-with-dependencies
```

2. Clean up the database entity schema for each store in the system:

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

4. Follow individual migration guides of the modules listed below:

* [Shipment](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-shipment.html#upgrading-from-version-6---to-version-7-0-0)
* [CustomerPage](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-customerpage.html#upgrading-from-version-1---to-version-2-0-0)

The following table lists the modules affected by the Split Delivery update:

| Module | Version | Migration guide |
| --- | --- | --- |
| `spryker/sales` | 11.0.0 | [Migration Guide - Sales](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-sales.html#upgrading-from-version-10---to-version-11-0-0) |
| `spryker/shipment` | 7.0.0 | [Migration Guide - Shipment](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-shipment.html#upgrading-from-version-6---to-version-7-0-0) |
| `spryker-shop/checkout-page` | 3.0.0 | [Migration Guide - CheckoutPage](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-checkoutpage.html#upgrading-from-version-2---to-version-3--) |
| `spryker-shop/customer-page` | 2.0.0 | [Migration Guide - CustomerPage](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-customerpage.html#upgrading-from-version-1---to-version-2-0-0) |
| `spryker/checkout-rest-api` | 2.0.0 | [Migration Guide - CheckoutRestApi](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/glue-api/migration-guide-checkoutrestapi.html#upgrading-from-version-1---to-version-2-0-0) |
| `spryker/manual-order-entry-gui` | 0.8.0 | [Migration Guide - ManualOrderEntryGui](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-manualorderentrygui.html#upgrading-from-version-0-7---to-version-0-8-0) |
| `spryker/shipment-cart-connector` | 2.0.0 | [Migration Guide - ShipmentCartConnector](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-shipmentcartconnector.html#upgrading-from-version-1-0---to-version-2-0-0) |
| `spryker/shipment-сheckout-сonnector` | 2.0.0 | [Migration Guide - ShipmentCheckoutConnector](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-shipmentcheckoutconnector.html#upgrading-from-version-1-0---to-version-2-0-0) |
| `spryker/shipment-discount-connector` | 4.0.0 | [Migration Guide - ShipmentDiscountConnector](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/migration-guide-shipmentdiscountconnector.html#upgrading-from-version-3-0---version-to-4-0-0) |
| `spryker/orders-rest-api` | 4.0.0 | [Migration Guide - OrdersRestApi](/docs/scos/dev/migration-and-integration/202009.0/module-migration-guides/glue-api/migration-guide-ordersrestapi.html#upgrading-from-version-3-0---to-version-4-0-0) |
