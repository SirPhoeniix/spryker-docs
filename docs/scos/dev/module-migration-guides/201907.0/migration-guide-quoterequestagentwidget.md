---
title: Migration Guide - QuoteRequestAgentWidget
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-quoterequestagentwidget
originalArticleId: 9fddd0af-cf1b-42e9-a7ce-7d4ec78130ed
redirect_from:
  - /v3/docs/mg-quoterequestagentwidget
  - /v3/docs/en/mg-quoterequestagentwidget
---

## Upgrading from Version 1.x.x to Version 2.x.x
The only major change of `QuoteRequestAgentWidget` 2.x.x is the dependency update for `spryker/quote-request-agent:^2.0.0`.

**To migrate, do the following:**
1. Update `spryker/quote-request-agent` to version ^2.0.0 by following the steps from [Migration Guide - QuoteRequestAgent](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-quoterequestagent.html).
2. Update `spryker-shop/quote-request-agent-widget:^2.0.0`

```bash
composer require spryker-shop/quote-request-agent-widget: "^2.0.0" --update-with-dependencies
```
*Estimated migration time: ~1h*
