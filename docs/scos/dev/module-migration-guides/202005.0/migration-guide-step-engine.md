---
title: Migration Guide - Step Engine
description: Use the guide to learn how to update the Step Engine module to a newer version.
last_updated: Apr 3, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/mg-step-engine
originalArticleId: 12ee3f56-2f54-43cb-8d1a-7c5366bcdc8a
redirect_from:
  - /v5/docs/mg-step-engine
  - /v5/docs/en/mg-step-engine
---

## Upgrading from Version 2.* to Version 3.*

If you're migrating the StepEngine module from version 2 to version 3, you need to follow the steps described below.
In Version 3 the `StepCollectionInterface::getPreviousStep()` has a new second optional argument (`AbstractTransfer $dataTransfer`). If you use this interface for your own implementation, you need to update your derived class.
If `StepEngineInterface::getTemplateVariables()` is overridden in your project, you need to update the call to `StepCollectionInterface::getPreviousStep()` here as well.

<!--See also:
[Defining a Step - Step Engine](https://documentation.spryker.com/capabilities/order_management/step_engine/step-engine-define-step.htm)-->
