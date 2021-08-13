---
title: Migration Guide - PriceProduct
description: Use the guide to migrate to a newer version of the PriceProduct module.
originalLink: https://documentation.spryker.com/2021080/docs/mg-priceproduct
originalArticleId: 40887521-7ada-48da-b160-7c9152e6a0a8
redirect_from:
  - /2021080/docs/mg-priceproduct
  - /2021080/docs/en/mg-priceproduct
  - /docs/mg-priceproduct
  - /docs/en/mg-priceproduct
---

## Upgrading from version 2.* to version 4.*
{% info_block infoBox %}
In order to dismantle the Horizontal Barrier and enable partial module updates on projects, a Technical Release took place. Public API of source and target major versions are equal. No migration efforts are required. Please [contact us](https://support.spryker.com/hc/en-us
{% endinfo_block %} if you have any questions.)

## Upgrading from version 1.* to version 2.*
There are new functionalities and changes that were added in this new module release. First of all, the changes imply implementation of the Price Dimension concept as well as adding of Service layer with PriceProductService. See [PriceProduct module details: Reference information](/docs/scos/dev/features/{{ page.version }}/prices/prices-feature-overview/priceproduct-module-details-reference-information.html#priceproductservice) for details.

In the previous version of the PriceProduct module, a product had only one price per store (and multi-currency) with gross and net amounts.
By adding the [Price dimension](/docs/scos/dev/features/{{ page.version }}/prices/prices-feature-overview/priceproduct-module-details-reference-information.html#price-dimension) concept to the new release, you can set specific prices for each customer separately. Having logged in, a user with these specific prices will see another prices in Catalog and will be able to buy products for  their own price.

To save BC, we have implemented Default Price Dimension inside the new `PriceProduct` module, so all prices imported by new `PriceProductDataImport` will be in the Default Price Dimension. See [Prices per Merchant Relation](/docs/scos/dev/features/{{ page.version }}/merchant-custom-prices-feature-overview.html) to learn more about the price dimension.
Prices from price dimensions could be stored not only in DB, but also in Storage. Therefore, the update of the PriceProductStorage module was necessary. The new version 2.0.0 of the PriceProduct module already supports price dimensions and has Default Price Dimension implemented.

To migrate the changes to the module, do the following:

1. Upgrade your database structure by running

```Bash
console propel:install
```

2. Enable the new `PriceProductDataImport` module:

    1. Remove project level `PriceProductDataImport` (`Pyz\Zed\DataImport\Business\Model\ProductPrice\ProductPriceWriterStep`) from `\Pyz\Zed\DataImport\Business\DataImportBusinessFactory`;
    2. Install the new importer module:

```Bash
composer install spryker/price-product-data-import
```
    3. Enable the module by adding
`\Spryker\Zed\PriceProductDataImport\Communication\Plugin\PriceProductDataImportPlugin` to `\Pyz\Zed\DataImport\DataImportDependencyProvider::getDataImporterPlugins()`

{% info_block infoBox "Customized PriceProductDataImport " %}

If you have customized `PriceProductDataImport` on the project level, you are still able to continue using it. The only thing you have to do is to add `$this->savePriceProductDefault($priceProductStoreEntity->getPrimaryKey());` at the end of your `PriceProductWriterStep`.

```php
/**
 * @param string $idPriceProductStore
 *
 * @return void
 */
protected function savePriceProductDefault(string $idPriceProductStore): void
{
    $priceProductDefaultEntity = SpyPriceProductDefaultQuery::create()
        ->filterByFkPriceProductStore($idPriceProductStore)
        ->findOneOrCreate();
    if ($priceProductDefaultEntity->isNew()) {
        $priceProductDefaultEntity->save();
    }
}
```

{% endinfo_block %}

3. Update PriceProductStorage by running

```Bash
composer require spryker/price-product-storage:"^2.0.0"
```

Now that the module supports plugins for reading prices from different price dimensions, you can put your own plugins here: 
`\Pyz\Client\PriceProductStorage\PriceProductStorageDependencyProvider::getPriceDimensionStorageReaderPlugins()`


