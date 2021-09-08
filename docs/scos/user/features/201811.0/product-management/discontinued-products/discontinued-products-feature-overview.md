---
title: Discontinued Products Feature Overview
description: Discontinued products are shown during a certain period of time after the manufacturer or a distributor announces that the product is no longer produced.
originalLink: https://documentation.spryker.com/v1/docs/discontinued-products-overview
originalArticleId: 6066f94b-0eea-4450-9071-a41b2cfa39e5
redirect_from:
  - /v1/docs/discontinued-products-overview
  - /v1/docs/en/discontinued-products-overview
---

## Out of Stock vs. Discontinued Products
While we try to keep all the items in stock, we occasionally run out of products. In such a case the concrete product is tagged as out of stock and cannot be added to cart:
![Discontinued PDP](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Product+Management/Discontinued+Products/Discontinued+Products+Feature+Overview/discontinued-pdp-page.png) 

Once the stock is updated with the positive number - the concrete product will be available for purchase.

Products are **discontinued** when the manufacturer or a current distributor has communicated that the product will no longer be produced. Still, the discontinued product may have stock (the stock number can either be positive or negative).

Discontinued products have a certain period of time when they will still be shown on the website (active_until). After this period ends - the products will become deactivated.

{% info_block warningBox %}
Only [concrete products](/docs/scos/dev/features/201811.0/product-management/product-abstraction.html#abstract-and-concrete-products--variants-
{% endinfo_block %} can become discontinued.)

The schema below illustrates the relations between discontinued products, abstract and concrete products:
![Module relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Product+Management/Discontinued+Products/Discontinued+Products+Feature+Overview/discontinued-schema.png) 

<!-- Last review date: Mar 1, 2019-- by Ahmed Sabaa, Yuliia Boiko -->