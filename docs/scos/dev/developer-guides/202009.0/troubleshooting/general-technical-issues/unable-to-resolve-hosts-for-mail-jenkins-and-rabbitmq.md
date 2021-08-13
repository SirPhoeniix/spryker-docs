---
title: Unable to resolve hosts for Mail, Jenkins, and RabbitMQ
description: Learn how to fix the issue with unresolved hosts for Mail, Jenkins, and RabbitMQ on Windows
originalLink: https://documentation.spryker.com/v6/docs/unable-to-resolve-hosts-for-mail-jenkins-and-rabbitmq
originalArticleId: 0971a16d-5186-4c8e-86cb-ec0b623cbd3f
redirect_from:
  - /v6/docs/unable-to-resolve-hosts-for-mail-jenkins-and-rabbitmq
  - /v6/docs/en/unable-to-resolve-hosts-for-mail-jenkins-and-rabbitmq
---

## Description

The issue occurs when setting up Docker and WSL 2 and adding routes to `etc/hosts` in one line on Windows. Host file has row 127.0.0.1.

## Cause
The cause of the issue might be in the maximum length limitaion of a line that you can have in your hosts file in Windows.

## Solution
In the hosts file, start a new line with `127.0.0.1`, and then add routes for services for which the hosts are not resolved.