---
title: SCSS linter integration guide
description: Learn how to integrate the SCSS linter into your project
last_updated: Feb 14, 2021
template: howto-guide-template
originalLink: https://documentation.spryker.com/v6/docs/scss-linter-integration-guide
originalArticleId: e6e5d05e-3722-4aa1-8d51-4567fc1ce700
redirect_from:
  - /v6/docs/scss-linter-integration-guide
  - /v6/docs/en/scss-linter-integration-guide
---

Follow the steps below to integrate the [SCSS linter ](/docs/scos/dev/sdk/{{page.version}}/development-tools/scss-linter.html)into your project.

## 1. Install the dependencies

To install the dependencies:
1. Install Stylelint:
```bash
npm install stylelint@13.7.x --save-dev
```
2. Install config for Stylelint:
```bash
npm install @spryker/frontend-config.stylelint --save-dev
```
3. Install the CLI parser:
```bash
npm install commander@4.0.x --save-dev
```

## 2. Update the scripts

To update the scripts:

1. Add the SCSS lint script to `/frontend/libs/stylelint.js`
```
const stylelint = require('stylelint');
const { globalSettings } = require('../settings');
const commandLineParser = require('commander');

commandLineParser
    .option('-f, --fix', 'execute stylelint in the fix mode.')
    .option('-p, --file-path <path>', 'execute stylelint only for this file.')
    .parse(process.argv);

const isFixMode = !!commandLineParser.fix;
const defaultFilePaths = [`${globalSettings.paths.project}/**/*.scss`];
const filePaths = commandLineParser.filePath ? [commandLineParser.filePath] : defaultFilePaths;

stylelint.lint({
    configFile: `${globalSettings.context}/node_modules/@spryker/frontend-config.stylelint/.stylelintrc.json`,
    files: filePaths,
    syntax: "scss",
    formatter: "string",
    fix: isFixMode,
}).then(function(data) {
    if (data.errored) {
        const messages = JSON.parse(JSON.stringify(data.output));
        process.stdout.write(messages);
        process.exit(1);
    }
}).catch(function(error) {
    console.error(error.stack);
    process.exit(1);
});
```
Check [here](https://github.com/spryker-shop/suite/blob/master/frontend/libs/stylelint.js) for the file example.

2.  Adjust the `/package.json` scripts:
```
"scripts": {
    ....
    "yves:stylelint": "node ./frontend/libs/stylelint",
    "yves:stylelint:fix": "node ./frontend/libs/stylelint --fix"
}
```
3. Add the ignore `file /.stylelintignore`:
```
# Ignore paths
**/node_modules/**
**/DateTimeConfiguratorPageExample/**
**/dist/**
public/*/assets/**
```
