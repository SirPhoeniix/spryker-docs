---
title: SCSS linter
description: Learn about the SCSS linter tool that allows you to find and fix mistakes in the code style.
last_updated: Feb 14, 2021
template: concept-topic-template
originalLink: https://documentation.spryker.com/v6/docs/scss-linter
originalArticleId: c5025de3-8f4f-4832-b39e-0c09da177889
redirect_from:
  - /v6/docs/scss-linter
  - /v6/docs/en/scss-linter
---

*SCSS linter* allows you to find and fix code style mistakes. It helps a team to follow the same standards and make code more readable.

To analyze and fix the existing SCSS files, [Stylelint](https://stylelint.io/) is used.

## Installation
For details on how to install the SCSS linter for your project, see the [SCSS linter integration guide](/docs/scos/dev/migration-and-integration/202009.0/development-tools/scss-linter-integration-guide.html).

## Using SCSS linter

To execute the SCSS linter, do the following:
1. Install the Node modules:

```bash
npm ci
```
2. Execute the SCSS linter in:
* validation mode:

```bash
npm run yves:stylelint
```
*  fix mode:
```bash
npm run yves:stylelint:fix
```
## SCSS linter config

The config for Stylelint resides in the [@spryker/frontend-config.stylelint](https://www.npmjs.com/package/@spryker/frontend-config.stylelint) module.

To redefine the path for the config file, adjust `/frontend/libs/stylelint.js`  and use other rules for the SCSS linter.

```
configFile: `${globalSettings.context}/node_modules/@spryker/frontend-config.stylelint/.stylelintrc.json`,
```

Also, the SCSS linter uses the ignore file `/.stylelintignore` that includes directories and files where the SCSS linter shouldn’t be executed.

{% info_block infoBox %}

SCSS linter rules related to formatting aren’t included in the [stylelint config](https://www.npmjs.com/package/@spryker/frontend-config.stylelint) to avoid duplication with the [Prettier rules](https://www.npmjs.com/package/@spryker/frontend-config.prettier).

{% endinfo_block %}

## CI checks and the pre-commit hook

The SCSS linter is integrated into:

* Pre-commit hooks
The function that executes the SCSS linter before the commit resides in `/.githook`:
```
- GitHook\Command\FileCommand\PreCommit\StyleLintCommand
```
* Travis
Command to run the SCSS linter is integrated into `.travis.yml`
```
- node ./frontend/libs/stylelint
```
{% info_block warningBox "Important" %}

If you commit without the pre-commit hooks, you should run the SCSS linter manually to avoid issues with Travis.

{% endinfo_block %}
{% info_block infoBox %}

Pre-commit hooks are integrated only in the Shop Suite and are not integrated in B2B and B2C Demo Shops.

{% endinfo_block %}


