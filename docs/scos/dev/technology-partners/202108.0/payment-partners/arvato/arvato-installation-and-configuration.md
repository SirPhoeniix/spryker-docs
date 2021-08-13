---
title: Arvato - Installation and Configuration
description: Provide complete and comprehensive risk management for the eCommerce/mail-order industry, contributing to a high level of modularization and automation.
originalLink: https://documentation.spryker.com/2021080/docs/arvato-installation-configuration
originalArticleId: 01e4a638-f2ea-4974-8f55-ee85d8745298
redirect_from:
  - /2021080/docs/arvato-installation-configuration
  - /2021080/docs/en/arvato-installation-configuration
  - /docs/arvato-installation-configuration
  - /docs/en/arvato-installation-configuration
---

{% info_block errorBox %}

There is currently an issue when using giftcards with Arvato. Our team is developing a fix for it.

{% endinfo_block %}
The purpose of developing the risk solution services is to provide a complete and comprehensive risk management for the eCommerce/mail-order industry, contributing to a high level of modularization and automation. Besides the use of pre-configured service modules for risk management, risk solution services comprise process support up to the  outsourcing of the entire operative risk management. All risk management processes are supported by a business intelligence component.
![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Arvato/arvato-rss-overview.png){height="" width=""}

## Prerequisites

For every service call of risk solution services an authorization is required.
The authorization data is transferred in the SOAP header and shows the following structure.

In order to send requests, you are supposed to have the following credentials, provided by Arvato:

| Parameter Name | Description |
| --- | --- |
| `ARVATORSS_URL` | Arvato RSS gateway. |
| `ClientID` | Unique client number in the risk solution services. Will be communicated to the client before the integration |
| `Authorization` | Password for the authorization at risk solution services |
| `ARVATORSS_PAYMENT_TYPE_MAPPING` | A map of payment names to ArvatoRss specific payment type codes. |

The following information (also present in `config.dist.php`) should be specified in configuration:
```php
 ArvatoRssConstants::ARVATORSS_URL =& '';
 ArvatoRssConstants::ARVATORSS_CLIENTID = '';
 ArvatoRssConstants::ARVATORSS_AUTHORISATION ='';
 // Mapping of your payment methods to payment types, that are known by Arvato Rss.
 ArvatoRssConstants::ARVATORSS_PAYMENT_TYPE_MAPPING => [
 'invoice' => ArvatoRssPaymentTypeConstants::INVOICE
 ];
 ```

API URLs:

| Name | URL |
| --- | --- |
| Production URL | `https://customer.risk-solution-services.de/rss-services/risk-solution-services.v2.1` |
| Sandbox URL | `https://integration.risk-solution-services.de/rss-services/risk-solution-services.v2.1` |

Services:
* [Risk Check](https://documentation.spryker.com/2021080/docs/arvato-risk-check-2-0)
* [Store Order](/docs/scos/dev/technology-partners/{{ page.version }}/payment-partners/arvato/arvato-store-order.html)

To implement Arvato RSS you should be familiar with concept of extending the

## Installation

### Composer Dependency

To install Arvato RSS module, use [Composer](https://getcomposer.org/):

```
composer require spryker-eco/arvato-rss
```