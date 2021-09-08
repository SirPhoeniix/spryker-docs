---
title: Product
description: Product Management system allows gathering product characteristics and exported them to Spryker. Products can be managed in the Back Office and displayed in Yves
originalLink: https://documentation.spryker.com/v4/docs/product
originalArticleId: 89dd1580-60de-4ed8-a80e-c9105d25a214
redirect_from:
  - /v4/docs/product
  - /v4/docs/en/product
---

Product is the central entity of a shop. Establishing the product data allows you to build and maintain a catalog representing your commercial offerings. The products are created and managed in the [ Back Office](/docs/scos/user/user-guides/202001.0/back-office-user-guide/general-back-office-overview.html). 
The product information you specify in the Back office, serves various purposes:

* Contains characteristics that describe the product.
* Affects the shop behavior. For example, filtering and search in your shop depend on the product attributes you set. 
* Used for internal calculations, such as, for example, delivery costs based on the product weight.

Besides the Spryker Back Office, product information can be maintained in an external **Product Information Management (PIM)** system. The data from the PIM systems can be exported to Spryker. An import interface transforms the incoming product data into the Spryker specific data structure and persists it. After that, the data is exported to Redis and Elasticsearch. This way, the Storefront (Yves) can access the relevant product data very fast. After the import has been finished, you can access the products in the Spryker Back Office (Zed).

![Product information management](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Product+Management/Product/product_information_management.png)

The Spryker Commerce OS supports integration of the following PIM systems:

* [Akeneo](/docs/scos/dev/developer-guides/202001.0/back-end-development/extending-spryker/extending-the-core.html)
* [Censhare PIM](/docs/scos/dev/technology-partners/202001.0/product-information-pimerp/censhare-pim.html)

