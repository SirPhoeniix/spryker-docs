---
title: CompanyUsersRestApi Migration Guide
last_updated: Jun 16, 2021
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/companyusersrestapi-migration-guide
originalArticleId: e34e7c88-d2e4-4a05-bef5-f49da84d9420
redirect_from:
  - /2021080/docs/companyusersrestapi-migration-guide
  - /2021080/docs/en/companyusersrestapi-migration-guide
  - /docs/companyusersrestapi-migration-guide
  - /docs/en/companyusersrestapi-migration-guide
---

## Upgrading from Version 1.3.0 to Version 2.0.0
In this version, the behavior of the `GET company-users` endpoint was changed. Now, it supports fetching of a single company user by uuid, a collection of company users available in a company, and a collection of Business-on-Behalf Company Users a user can impersonate as.
Adjust your code to use new functionality:
1. If you were using the `/company-users` endpoint to get available Business-on-Behalf Company Users, change it to `/company-users/mine`.

1. Regenerate transfer objects:

```php
vendor/bin/console transfer:generate
```

3. Make sure that database schema is up to date:

```php
vendor/bin/console propel:install
vendor/bin/console transfer:generate
```

*Estimated migration time: ~5 minutes*
