---
title: Klarna - Payment Workflow
description: In this article, you will find part payment request flow with Klarna.
last_updated: Nov 22, 2019
template: concept-topic-template
originalLink: https://documentation.spryker.com/v4/docs/klarna-payment-workflow
originalArticleId: c6db9ec4-75d0-469f-8e64-cda0ece7ded5
redirect_from:
  - /v4/docs/klarna-payment-workflow
  - /v4/docs/en/klarna-payment-workflow
related:
  - title: Klarna - Invoice Pay in 14 days
    link: docs/scos/user/technology-partners/page.version/payment-partners/klarna/technical-details-and-howtos/klarna-invoice-pay-in-14-days.html
  - title: Klarna
    link: docs/scos/user/technology-partners/page.version/payment-partners/klarna/klarna.html
  - title: Klarna - Part Payment Flexible
    link: docs/scos/user/technology-partners/page.version/payment-partners/klarna/technical-details-and-howtos/klarna-part-payment-flexible.html
  - title: Klarna - State Machine Commands and Conditions
    link: docs/scos/user/technology-partners/page.version/payment-partners/klarna/technical-details-and-howtos/klarna-state-machine-commands-and-conditions.html
---

Both `Part Payment` and `Invoice` payment methods have the same request flow. It basically consists of the following steps:

* Pre-check: reserves the amount of the purchase
* Check order status: checks if the order status is `pending accepted`. If it's not, OMS waits for 2 hours and then calls again `KlarnaApi` to retrieve the status of the order. In case the status is `denied` the order is canceled.
* Capture payment: activates the reservation that corresponds to the given reference number
* Update payment: if activation fails, we need to update the reservation that corresponds to the given reference number
* Refund: performs a partial refund.
* Cancel: cancels a reservation.
