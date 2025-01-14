---
title: Migration Guide - Category Template Migration Console
last_updated: Aug 27, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/mg-category-template-console
originalArticleId: ef2a80e2-a876-4c56-820d-5e8d7c9a44f7
redirect_from:
  - /v6/docs/mg-category-template-console
  - /v6/docs/en/mg-category-template-console
---

## Category Template Migration Script

```php
<?php

/**
 * Copyright © 2016-present Spryker Systems GmbH. All rights reserved.
 * Use of this software requires acceptance of the Evaluation License Agreement. See LICENSE file.
 */

namespace Pyz\Zed\Category\Communication\Console;

use Exception;
use Orm\Zed\Category\Persistence\SpyCategoryQuery;
use Orm\Zed\Category\Persistence\SpyCategoryTemplateQuery;
use Spryker\Zed\Category\CategoryConfig;
use Spryker\Zed\Kernel\Communication\Console\Console;
use Spryker\Zed\PropelOrm\Business\Runtime\ActiveQuery\Criteria;
use Symfony\Component\Console\Input\InputInterface;
use Symfony\Component\Console\Output\OutputInterface;

/**
 * @method \Spryker\Zed\Category\Business\CategoryFacadeInterface getFacade()
 */
class CategoryTemplateMigration extends Console
{

    const COMMAND_NAME = 'category-template:migrate';

    /**
     * @var \Symfony\Component\Console\Output\OutputInterface
     */
    protected $output;

    /**
     * @param \Symfony\Component\Console\Input\InputInterface $input
     * @param \Symfony\Component\Console\Output\OutputInterface $output
     *
     * @return void
     */
    public function execute(InputInterface $input, OutputInterface $output)
    {
        $this->output = $output;

        $this->getFacade()->syncCategoryTemplate();
        $this->assignTemplateToAllCategories();

        $output->writeln('Successfully finished.');
    }

    /**
    * @return void
    */
    protected function configure()
    {
        parent::configure();

        $this->setName(static::COMMAND_NAME);
        $this->setDescription('');
    }

    /**
    * @throws \Exception
    *
    * @return void
    */
    protected function assignTemplateToAllCategories()
    {
        $spyCategoryTemplate = SpyCategoryTemplateQuery::create()
            ->filterByName(CategoryConfig::CATEGORY_TEMPLATE_DEFAULT)
            ->findOne();

        if (empty($spyCategoryTemplate)) {
            throw new Exception('Please specify CATEGORY_TEMPLATE_DEFAULT in your category template list configuration');
        }

        $query = SpyCategoryQuery::create()
            ->filterByFkCategoryTemplate(null, Criteria::ISNULL);

        $this->output->writeln('Will update ' . $query->count() . ' categories without template.');

        foreach ($query->find() as $category) {
            $category->setFkCategoryTemplate($spyCategoryTemplate->getIdCategoryTemplate());
            $category->save();
        }
    }

    /**
    * @return array
    */
    protected function getTemplateList()
    {
        return $this->getFactory()
                ->getConfig()
                ->getTemplateList();
    }

}
```

<!--See also
Get a general idea about a Category
Migration Guide - Category-->
