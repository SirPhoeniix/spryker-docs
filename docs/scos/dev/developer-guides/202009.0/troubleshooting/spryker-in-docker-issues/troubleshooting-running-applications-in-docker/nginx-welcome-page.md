---
title: Nginx welcome page
description: Learn how to fix the issue when you get Nginx welcome page upon opening an application in browser
originalLink: https://documentation.spryker.com/v6/docs/nginx-welcome-page
originalArticleId: 9ecca499-90a3-41d6-9bbd-660545c7cf79
redirect_from:
  - /v6/docs/nginx-welcome-page
  - /v6/docs/en/nginx-welcome-page
---

You get the Nginx welcome page by opening an application in the browser.

1. Update the nginx:alpine image:

```bash
docker pull nginx:alpine
```

2. Re-build applications:

```bash
docker/sdk up
```