---
title: Marketplace Inventory Management + Packaging Units feature integration
last_updated: Dec 16, 2020
summary: This document describes the process how to integrate the Marketplace Inventory Management + Packaging Units feature into a Spryker project.
---

## Install feature Core
Follow the steps below to install the Marketplace Inventory Management + Packaging Units feature core.

### Prerequisites
To start feature integration, overview and install the necessary features:

| NAME | VERSION | LINK |
|-|-|-|
| Spryker Core | master | [[PUBLISHED] Glue API: Spryker Core feature integration - ongoing]()  |
| Marketplace Inventory Management | master | [[WIP] Marketplace Inventory Management Feature Integration - ongoing]()  |
| Marketplace Inventory Management + Order Management Feature Integration | master | [[WIP] Marketplace Inventory Management + Order Management Feature Integration]()  |

### 1) Install the required modules using Composer
Run the following commands to install the required modules:

```bash
composer require spryker/product-offer-packaging-unit:"^0.1.0" --update-with-dependencies
```

Make sure that the following modules have been installed:

| MODULE | EXPECTED DIRECTORY |
|-|-|
| ProductOfferPackagingUnit | vendor/spryker/product-offer-packaging-unit |

### 2) Set up behavior
#### Enable resources and relationships
Activate the following plugins:

| PLUGIN | SPECIFICATION | PREREQUISITES | NAMESPACE |
|-|-|-|-|
| ProductOfferPackagingUnitOmsReservationAggregationPlugin | Aggregates reservations for product offers packaging unit. | None | Spryker\Zed\ProductOfferPackagingUnit\Communication\Plugin\Oms |

**src/Pyz/Zed/Oms/OmsDependencyProvider.php**

```php
<?php

namespace Pyz\Zed\Oms;

use Spryker\Zed\Oms\OmsDependencyProvider as SprykerOmsDependencyProvider;
use Spryker\Zed\ProductOfferPackagingUnit\Communication\Plugin\Oms\ProductOfferPackagingUnitOmsReservationAggregationPlugin;

class OmsDependencyProvider extends SprykerOmsDependencyProvider
{
    /**
     * @return \Spryker\Zed\OmsExtension\Dependency\Plugin\OmsReservationAggregationPluginInterface[]
     */
    protected function getOmsReservationAggregationPlugins(): array
    {
        return [
            new ProductOfferPackagingUnitOmsReservationAggregationPlugin(),
        ];
    }
}
```

Make sure that availability calculated properly for the product offers that belong to product with packaging units.

* Add such product offer to the cart.
* Place order.
* Make sure that `spy_product_offer_reservation` contains new row which have reserved the quantity equal bought packaging unit amount.