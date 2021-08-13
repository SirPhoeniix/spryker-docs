---
title: Setting up Tests
description: Learn how to set up an efficient organization for your tests.
originalLink: https://documentation.spryker.com/2021080/docs/setting-up-tests
originalArticleId: c8894db9-1871-41a4-a1fc-2c57d8de84c2
redirect_from:
  - /2021080/docs/setting-up-tests
  - /2021080/docs/en/setting-up-tests
  - /docs/setting-up-tests
  - /docs/en/setting-up-tests
---

To get all the things working, you need to prepare a proper organization for your tests. For this, you, first of all, have the root `codeception.yml` file . Its main responsibility is to include other `codecpetion.yml` files that contain the suite configuration. See [Configuration](/docs/scos/dev/developer-guides/{{ page.version }}/development-guide/guidelines/testing/test-framework.html#configuration) for details.

### Directory Structure
To organize your tests, follow this structure of the tests directory:

```
tests/
    PyzTest/
        ApplicationA/
            ModuleA/
                Communication/
                Presentation/
                ...
                codeception.yml
        ApplicationB
            ModuleA
                Communication/
                Presentation/
                Business/
                ...
                codeception.yml
```

Check out the organization within the [tests/PyzTest/](https://github.com/spryker-shop/suite/tree/master/tests/PyzTest) directory in Spryker Master Suite for example.

Together with the [root configuration](/docs/scos/dev/developer-guides/{{ page.version }}/development-guide/guidelines/testing/test-framework.html#configuration), you are now able to organize your tests in a way that each test suite can have its own helper applied and can be executed separately.

## Next Steps
* Learn about the [available test helpers](/docs/scos/dev/developer-guides/{{ page.version }}/development-guide/guidelines/testing/available-test-helpers.html).
* [Create or enable a test helper](/docs/scos/dev/developer-guides/{{ page.version }}/development-guide/guidelines/testing/test-helpers.html).

               