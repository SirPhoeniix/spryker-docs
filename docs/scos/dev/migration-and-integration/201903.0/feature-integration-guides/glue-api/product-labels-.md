---
title: Product Labels API Feature Integration
originalLink: https://documentation.spryker.com/v2/docs/product-labels-api-feature-integration-201903
redirect_from:
  - /v2/docs/product-labels-api-feature-integration-201903
  - /v2/docs/en/product-labels-api-feature-integration-201903
---

Follow the steps below to install Product Labels Feature API.

### Prerequisites
To start feature integration, overview and install the necessary features:

| Name | Version | Required Sub-Feature |
| --- | --- | --- |
| Spryker Core | 201903.0 | [Glue Application Feature Integration](https://documentation.spryker.com/v2/docs/glue-application-feature-integration-201903) |
| Product Management | 201903.0 | [Products API Feature Integration](https://documentation.spryker.com/v2/docs/product-api-feature-integration-201903) |
| Product Label | 201903.0 | |


## 1) Install the Required Modules Using Composer

Run the following command to install the required modules:

```bash
composer require spryker/product-labels-rest-api:"^1.0.1" --update-with-dependencies
```

<section contenteditable="false" class="warningBox"><div class="content">
    Make sure that the following module is installed:

| Module | Expected Directory |
| --- | --- |
| `ProductLabelsRestApi` | `vendor/spryker/product-labels-rest-api` |
</div></section>

## 2) Set up Transfer Objects

Run the following commands to generate transfer changes:

```bash
console transfer:generate
```

<section contenteditable="false" class="warningBox"><div class="content">
    Make sure that the following changes are present in transfer objects:

| Transfer | Type | Event | Path |
| --- | --- | --- | --- |
| `RestProductLabelsAttributesTransfer` | class | created | `	src/Generated/Shared/Transfer/RestProductLabelsAttributesTransfer` |
</div></section>

## 3) Set up Behavior
Set up the following behaviors.

### Enable Resources and Relationships

Activate the following plugin:

| Plugin | Specification |Prerequisites  |Namespace  |
| --- | --- | --- | --- |
| `ProductLabelsRelationshipByResourceIdPlugin` | Adds the product labels resource as a relationship to the abstract product resource. | None | `Spryker\Glue\ProductLabelsRestApi\Plugin\GlueApplication\ProductLabelsRelationshipByResourceIdPlugin` |
| `ProductLabelsResourceRoutePlugin` |Registers the product labels resource.  | None | `Spryker\Glue\ProductLabelsRestApi\Plugin\GlueApplication\ProductLabelsResourceRoutePlugin` |

<details open>
<summary>src/Pyz/Glue/GlueApplication/GlueApplicationDependencyProvider.php</summary>

```php
<?php
 
namespace Pyz\Glue\GlueApplication;
 
use Spryker\Glue\GlueApplication\GlueApplicationDependencyProvider as SprykerGlueApplicationDependencyProvider;
use Spryker\Glue\ProductLabelsRestApi\Plugin\GlueApplication\ProductLabelsRelationshipByResourceIdPlugin;
use Spryker\Glue\ProductLabelsRestApi\Plugin\GlueApplication\ProductLabelsResourceRoutePlugin;
use Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface;
 
class GlueApplicationDependencyProvider extends SprykerGlueApplicationDependencyProvider
{
    /**
     * @return \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRoutePluginInterface[]
     */
    protected function getResourceRoutePlugins(): array
    {
        return [
            new ProductLabelsResourceRoutePlugin(),
        ];
    }
 
    /**
    * @param \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface $resourceRelationshipCollection
    *
    * @return \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface
    */
    protected function getResourceRelationshipPlugins(
        ResourceRelationshipCollectionInterface $resourceRelationshipCollection
    ): ResourceRelationshipCollectionInterface {
         $resourceRelationshipCollection->addRelationship(
            ProductsRestApiConfig::RESOURCE_ABSTRACT_PRODUCTS,
            new ProductLabelsRelationshipByResourceIdPlugin()
        );
 
        return $resourceRelationshipCollection;
    }
}
```

</br>
</details>

{% info_block warningBox "Verification" %}

Make sure the following endpoint is available: `http://glue.mysprykershop.com/product-labels/{% raw %}{{{% endraw %}abstract_sku{% raw %}}}{% endraw %}`


Send a request to `http://mysprykershop.com/abstract-products/{% raw %}{{{% endraw %}sku{% raw %}}}{% endraw %}?include=product-labels `and verify if the abstract product with the given SKU has at least one assigned product label and the response includes relationships to the product-labels resources.

{% endinfo_block %}
