---
title: Zed API Configuration
description: The article describes how you can configure API for Zed.
last_updated: Nov 22, 2019
template: concept-topic-template
originalLink: https://documentation.spryker.com/v4/docs/zed-api-config
originalArticleId: 9de12db6-a316-4118-b655-67d15e72bf46
redirect_from:
  - /v4/docs/zed-api-config
  - /v4/docs/en/zed-api-config
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
