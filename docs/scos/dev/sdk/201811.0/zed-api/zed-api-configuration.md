---
title: Zed API Configuration
last_updated: Nov 11, 2019
template: concept-topic-template
originalLink: https://documentation.spryker.com/v1/docs/zed-api-config
originalArticleId: 767325d9-ab9d-4a8b-8b9a-05e46a7a7fd1
redirect_from:
  - /v1/docs/zed-api-config
  - /v1/docs/en/zed-api-config
---

First of all we need to decide on the resources being exposed. Those will be mapped inside the `ApiDependencyProvider`:

```php
<?php
use Spryker\Zed\CustomerApi\Communication\Plugin\Api\CustomerApiResourcePlugin;
use Spryker\Zed\ProductApi\Communication\Plugin\Api\ProductApiResourcePlugin;

    /**
     * @return \Spryker\Zed\Api\Dependency\Plugin\ApiResourcePluginInterface[]
     */
    protected function getApiResourcePluginCollection()
    {
        return [
            new CustomerApiResourcePlugin(),
            new ProductApiResourcePlugin(),
            ...
        ];
    }

```

Each resource plugin contains a `getResourceName()` which will map to the resource name of the URL. Those can also be versioned or customized if necessary.

Example: If you create a `CustomerApiResourcePlugin` containing `customer-groups` as a resource name, the API resource URL is then API prefix (/api/rest/) + resource name, in this case `/api/rest/customer-groups`.
