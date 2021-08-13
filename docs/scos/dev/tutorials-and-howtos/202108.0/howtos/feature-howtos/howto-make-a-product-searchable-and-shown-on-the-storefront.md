---
title: HowTo - Make a Product Searchable and Shown on the Storefront
description: Use the guide to learn about conditions need to be performed to make a product searchable in the online store.
originalLink: https://documentation.spryker.com/2021080/docs/ht-make-product-shown-on-frontend-by-url
originalArticleId: c8a71f89-7fea-4bd5-9c50-3f372b8af760
redirect_from:
  - /2021080/docs/ht-make-product-shown-on-frontend-by-url
  - /2021080/docs/en/ht-make-product-shown-on-frontend-by-url
  - /docs/ht-make-product-shown-on-frontend-by-url
  - /docs/en/ht-make-product-shown-on-frontend-by-url
---

{% info_block infoBox %}
The article describes the flow on how to make a product searchable and displayed on the Storefront.
{% endinfo_block %}

There are a number of conditions that should be fulfilled to make your product searchable and shown on Yves by URL. What is important is to make sure that your product meets the following conditions:

* It is assigned to categories. See the [Category](/docs/scos/user/user-guides/{{ page.version }}/back-office-user-guide/catalog/category/assigning-products-to-categories.html) section for details on how to assign products to categories.
* It is in stock in the warehouse for the current store. See the [Availability](/docs/scos/user/user-guides/{{ page.version }}/back-office-user-guide/catalog/availability/managing-products-availability.html) section to learn how to check products' availability.
* The product's status is **Active**. See the [Products](/docs/scos/user/user-guides/{{ page.version }}/back-office-user-guide/catalog/products/managing-products/managing-products.html#activating-a-product) section to learn how to manage products, including status change.
* It has a price in the current locale. See the [Products](/docs/scos/user/user-guides/{{ page.version }}/back-office-user-guide/catalog/products/managing-products/managing-products.html) section for more details.
* It has been marked as searchable in the Back Office. See the [Products](/docs/scos/user/user-guides/{{ page.version }}/back-office-user-guide/catalog/products/concrete-products/creating-a-product-variant.html) section for more details
* It has product variants - abstract product will not be displayed on Yves unless it has product variants. See [Products](/docs/scos/user/user-guides/{{ page.version }}/back-office-user-guide/catalog/products/concrete-products/creating-a-product-variant.html) to learn how to create product variants.