---
title: Migration Guide - CmsPageSearch
last_updated: Sep 14, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/mg-cmspagesearch
originalArticleId: d74fd7dc-0587-4e46-be56-9bf500764ce2
redirect_from:
  - /v5/docs/mg-cmspagesearch
  - /v5/docs/en/mg-cmspagesearch
---

## Upgrading from Version 2.1.* to Version 2.2.*
{% info_block errorBox "Prerequisites" %}

This migration guide is a part of the [Search migration effort](/docs/scos/dev/migration-concepts/search-migration-concept/search-migration-concept.html). Prior to upgarding this module, make sure you have completed all the steps from the [Search Migration Guide](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-search.html#upgrading-from-version-8-9---to-version-8-10--). 

{% endinfo_block %}
To upgrade the module, do the following:
1. Update the module with composer:
```bash
composer update spryker/cms-page-search
```
2. Remove all deprecated query expander plugins coming from the Search module (if any) from `Pyz\Client\CmsPageSearch\CmsPageSearchDependencyProvider`:
```php
Spryker\Client\Search\Plugin\Elasticsearch\QueryExpander\IsActiveInDateRangeQueryExpanderPlugin
Spryker\Client\Search\Plugin\Elasticsearch\QueryExpander\IsActiveQueryExpanderPlugin
Spryker\Client\Search\Plugin\Elasticsearch\QueryExpander\LocalizedQueryExpanderPlugin
Spryker\Client\Search\Plugin\Elasticsearch\QueryExpander\StoreQueryExpanderPlugin
```
3. Enable the replacement plugins:

Pyz\Client\CmsPageSearch
   
```php
<?php

namespace Pyz\Client\CmsPageSearch;

...
use Spryker\Client\CmsPageSearch\CmsPageSearchDependencyProvider as SprykerCmsPageSearchDependencyProvider;
use Spryker\Client\SearchElasticsearch\Plugin\QueryExpander\IsActiveInDateRangeQueryExpanderPlugin;
use Spryker\Client\SearchElasticsearch\Plugin\QueryExpander\IsActiveQueryExpanderPlugin;
use Spryker\Client\SearchElasticsearch\Plugin\QueryExpander\LocalizedQueryExpanderPlugin;
use Spryker\Client\SearchElasticsearch\Plugin\QueryExpander\StoreQueryExpanderPlugin;

class CmsPageSearchDependencyProvider extends SprykerCmsPageSearchDependencyProvider
{
    ...
    
    /**
     * @return \Spryker\Client\SearchExtension\Dependency\Plugin\QueryExpanderPluginInterface[]
     */
    protected function createCmsPageSearchQueryExpanderPlugins(): array
    {
        return [
            ...
            new StoreQueryExpanderPlugin(),
            new LocalizedQueryExpanderPlugin(),
            new IsActiveQueryExpanderPlugin(),
            new IsActiveInDateRangeQueryExpanderPlugin(),
        ];
    }

    /**
     * @return \Spryker\Client\SearchExtension\Dependency\Plugin\QueryExpanderPluginInterface[]
     */
    protected function createCmsPageSearchCountQueryExpanderPlugins(): array
    {
        return [
            new StoreQueryExpanderPlugin(),
            new LocalizedQueryExpanderPlugin(),
            new IsActiveQueryExpanderPlugin(),
            new IsActiveInDateRangeQueryExpanderPlugin(),
        ];
    }
}  
```

4. Remove the deprecated plugin usages listed below from `Pyz\Zed\Search\SearchDependencyProvider`:
```php
Spryker\Zed\CmsPageSearch\Communication\Plugin\Search\CmsDataPageMapBuilder
```
## Upgrading from Version 1.* to Version 2.*
Version 2.0.0 of the CmsPageSearch module introduces the [multi-store functionality](https://documentation.spryker.com/v5/docs/en/cms-pages-overview). The multi-store CMS page feature enables management of CMS page display per store via a store toggle control in the Back Office.

To avoid the BC break, a synchronization behavior must be removed.

**To upgrade to the new version of the module, do the following:**
1. Update `cms-page-search` to `^2.0.0` with the command: `composer update spryker/cms-page-search:^2.0.0`
2. Remove `queue_pool=synchronizationPool` behavior from the `spy_cms_page_search` table.
`src/Pyz/Zed/CmsPageSearch/Persistence/Propel/Schema/spy_cms_page_search.schema.xml<behavior name="synchronization"><parameter name="queue_pool" value="synchronizationPool" /></behavior>`
{% info_block infoBox %}
When completed, the above synchronization parameter should not be in the file.
{% endinfo_block %}
3. Apply the database changes:
`$ console propel:install`
4. Generate new transfers:
`$ console transfer:generate`

_Estimated migration time: 30 minutes_

<!-- Last review date: Mar 12, 2019- by Alexander Veselov, Yuliia Boiko -->
