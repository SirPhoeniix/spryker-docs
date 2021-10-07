---
title: Arvato - Risk Check
description: Arvato Risk Check evaluates the probability of payment default for the customer orders.
originalLink: https://documentation.spryker.com/v6/docs/arvato-risk-check
originalArticleId: a3ad6190-46ca-4a2f-af7c-0ad5b96bca19
redirect_from:
  - /v6/docs/arvato-risk-check
  - /v6/docs/en/arvato-risk-check
---

Accounted for by external credit agency data and internal existing customer- and order-details the `RiskCheck` evaluates the probability of payment default for the customer orders.

The returned decision codes (`Result` – `ActionCode` – `ResultCode`) manage the definition of the eShop's payment methods.
If a payment method is not permitted, the decision code provides information about alternate payment methods available for the customer.

 Additional validation of billing and shipping addresses is performed on Arvato RSS side. Please refer to Arvato documentation for return code bit pattern and explanation of bits.

The main entry point to risk check functionality is `performRiskCheck` method inside `ArvatoRssFacade` class.

Developer is supposed to call `performRiskCheck` method providing actual `QuoteTransfer` as the first argument.
In the response `QuoteTransfer` is returned with `ArvatoRssRiskCheckResponse` transfer inside. It contains `Result`, `ResultCode`, `ActionCode`, `ResultText`, `billingAddressValidation`, `deliveryAddressValidation`.

Response can be taken with:
```php
 $quoteTransfer->getArvatoRssQuoteData()->getArvatoRssRiskCheckResponse();
 ```
{% info_block warningBox "Note" %}
The transfer can have all fields empty if error occurred during request.
{% endinfo_block %}

<b>Data, that is sent to Arvato RSS and must be present in quote:</b>

| Name | Notes |
| --- | --- |
|  `Country` | Is taken from `BillingAddress` and `ShippingAddress` |
|  `City` | Is taken from `BillingAddress` and `ShippingAddress` |
|  `Street` | Is taken from `BillingAddress` and `ShippingAddress` |
|  `StreetNumber` | Is taken from `BillingAddress` and `ShippingAddress` |
|  `ZipCode` | Is taken from `BillingAddress` and `ShippingAddress` |
|  `FirstName` | Is taken from `BillingAddress` and `ShippingAddress` |
|  `LastName` | Is taken from `BillingAddress` and `ShippingAddress` |
|  `RegisteredOrder` | Shows if order is placed with registered customer or not. |
|  `Currency` | Is taken from store configuration |
|  `GrossTotalBill` | Total value of order incl. delivery fee, rebates/ credit notes and VAT (Grand Total) |
|  `TotalOrderValue` | Value of goods for this order incl. VAT (Subtotal) |
|  `ProductNumber` | Product number, defined by customer(default value 1). Sku is set there. |
|  `ProductGroupId` | Product group number/product type (default value 1). 1 is set. |
|  `UnitPrice` | Value of units incl. VAT. It is taken from `ItemTransfer`. |
|  `UnitCount` | Quantity of units (maximum value 99999999). It is taken from `ItemTransfer` |

You can check the result codes, returned by Arvato in the attachment.

@(Embed)(https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Arvato/arvato-rss-result-codes.xlsx)