---
title: Creating marketplace abstract products
last_updated: Aug 11, 2021
description: This document describes how to create marketplace abstract products in the Merchant Portal.
template: back-office-user-guide-template
---

This document describes how to create marketplace abstract products.

## Prerequisites

To start working with marketplace abstract products, go to **Merchant Portal > Products**.

This article contains reference information. Make sure to review it before you start, or just look up the necessary information as you go through the process.

## Creating a marketplace abstract product

To create a new abstract product:

1. On the *Products* page, click **Create Product**. *Create Abstract Product* drawer opens.

2. Define the following settings:

   1. Enter an **SKU Prefix**.

   2. Enter a **Name** for the default locale. The rest of the locales will be defined once the product is created.

   3. Select **Abstract product has 1 concrete product** if you are creating an abstract product that doesn't require variants. *Create an Abstract Product with 1 Concrete Product* drawer opens.

   {% info_block warningBox "Warning" %}

   It is not possible to save the abstract product unless it is accompanied by at least one concrete product.

   {% endinfo_block %}


   Select **Abstract product has multiple concrete products** if the abstract product you are creating will require variants.

   4. Click **Next**. <br>

   <br>

      If you chose **Abstract product has 1 concrete product**:<br>


      1. On the *Create an Abstract Product with 1 Concrete Product* drawer, enter a **Concrete Product SKU**.
      2. Enter a **Concrete Product Name**.
      3. To finish the product creation, click **Create**.



      ![img](https://spryker.s3.eu-central-1.amazonaws.com/docs/User+Guides/merchant+portal+user+guides/Products/create-abstract-product-with-one-variant-mp.gif)



      If you chose **Abstract product has multiple concrete products**:<br>

   <br>

      1. Select a super attribute that defines the variation of your concrete products.
      2. In the field next to the super attribute you've selected, select one or more values for each super attribute. Upon adding the super attribute values, the preview of the concrete products is displayed.

      {% info_block infoBox "Info" %}

      Removing a super attribute or its value removes the related concrete products or concrete product values from the preview.

      {% endinfo_block %}

      1. Optional: Add more super attributes by clicking the **Add** button. Repeat this step until you select at least one value for each selected super attribute.

      ![img](https://spryker.s3.eu-central-1.amazonaws.com/docs/User+Guides/merchant+portal+user+guides/Products/create-abstract-product-with-multiple-variants-mp.gif)

      {% info_block infoBox "Info" %}

      You can remove a concrete product from the preview list by clicking the **Remove** icon.

      {% endinfo_block %}

3. Once done, click **Create**.


Once the product is created, it needs to be [activated](/docs/marketplace/user/merchant-portal-user-guides/{{page.version}}/products/concrete-products/managing-marketplace-concrete-product.html#activating-and-deactivating-a-concrete-product). Only active marketplace products are displayed on the Marketplace Storefront.

### Reference information: Create abstract product

| ATTRIBUTE             | DESCRIPTION       |
| ----------------------------- | ------------------------------------ |
| SKU prefix                                      | Unique abstract product identifier that is used to track unique information related to the product.|
| Name                                            | The name of the abstract product that is displayed for the product on the Storefront. |
| Abstract product has 1 concrete product         | Select this option when you want your abstract product to have a single concrete product. |
| Abstract product has multiple concrete products | Select this option when you want your abstract product to have multiple concrete products. |

### Reference information: Create an Abstract Product with 1 Concrete Product

| ATTRIBUTE            | DESCRIPTION             |
| --------------------- | ------------------------------------ |
| Concrete Product SKU     | Unique product identifier that is used to track unique information related to the product. |
| Autogenerate SKU         | Check the box if you want the SKU to be generated automatically. By default, -1 is added to the abstract product SKU prefix. For example, `product-1` |
| Concrete Product Name    | The name of the concrete product that is displayed for the product on the Storefront. |
| Same as Abstract Product | Check the box if you want the name of the abstract product to be used for the concrete product as well. |

### Reference information: Create an Abstract Product with multiple Concrete Products

You can select as many super attributes as you need and define one or more values for them. When you select a product attribute value, a concrete product based on this value is displayed. In the *Concrete Products’ Preview* pane you can view the products to be created.

By selecting **Autogenerate SKUs**, the SKU numbers for the variants are generated automatically, based on the SKU prefix of their abstract product.

By selecting **Same Name as Abstract Product**, the name of the abstract product is used for the concrete products as well.

## Next steps

- [Manage abstract product](/docs/marketplace/user/merchant-portal-user-guides/{{ page.version }}/products/abstract-products/managing-marketplace-abstract-product.html)
