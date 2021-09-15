---
title: Migration Guide - SharedCartPage
originalLink: https://documentation.spryker.com/v2/docs/mg-shared-cart-page
originalArticleId: 4a3e9cf9-f23a-4f17-9b9c-497a8c67d179
redirect_from:
  - /v2/docs/mg-shared-cart-page
  - /v2/docs/en/mg-shared-cart-page
---

## Upgrading from Version 1.* to Version 2.*
From version 2 we have removed the disabled users from the shared list. The ability to enable/disable users was added to the `CompanyUser` module, version 2.0.0.

**To upgrade to the new version of the module, do the following:**
1. Upgrade the `CompanyUser` module to version 2.0.0. See [Migration Guide - CompanyUser](https://docs.demo-spryker.com/v4/docs/mg-companyuser) for more details:

```yaml
composer require spryker/company-user: “^2.0.0”
```
2. Regenerate transfer objects:

```yaml
vendor/bin/console transfer:generate
```

*Estimated migration time: 10 minutes*
 
<!-- Last review date: Feb 4, 2019* -by Sergey Samoylov, Yuliia Boiko--> 