---
title: Creating a New Custom Scheduler
description: This tutorial describes how to create a new custom scheduler.
originalLink: https://documentation.spryker.com/v4/docs/ht-create-a-new-custom-scheduler
originalArticleId: 8031a507-31ab-4c37-9419-35675cb42322
redirect_from:
  - /v4/docs/ht-create-a-new-custom-scheduler
  - /v4/docs/en/ht-create-a-new-custom-scheduler
---

To create a new custom scheduler:

1. Create a reader plugin that reads configuration of jobs from the specific source.
2. Create an adapter plugin that covers the basic scheduler functionality.
3. Enable plugins in `\Pyz\Zed\Scheduler\SchedulerDependencyProvider` and adjust configuration settings according to your changes.


<!--*Last review date: Oct 29, 2019* by Oleksandr Myrnyi, Andrii Tserkovnyi-->

