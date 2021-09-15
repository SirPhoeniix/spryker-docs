---
title: Back in Stock Notification Feature Overview
description: The feature allows both registered and guest users to subscribe to the newsletter by specifying the email address they wish to receive the notifications to
originalLink: https://documentation.spryker.com/v2/docs/back-in-stock-notification-feature-overview
originalArticleId: 0a487199-c3aa-4c53-9855-5a65b6c1524d
redirect_from:
  - /v2/docs/back-in-stock-notification-feature-overview
  - /v2/docs/en/back-in-stock-notification-feature-overview
---

When a customer visits a page of a product which is out of stock, they usually search for the shop which has the product in stock. The Back Office user of the original store will replenish the stock, however, it does not mean that the customer will still be there to buy it. The **Product is available again** feature provides a way to notify you about the demand for the product, so you can prioritize the product replenishment, as well as notify the customer once it is done.

The feature works in a form of a newsletter for both guest users and registered ones. Guest users subscribe by entering the email address they would like to receive the notification to:
![Guest subscription](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Mailing+&+Communication/Product+is+Available+Again/guest-subscription.png) 

Registered users subscribe to the newsletter in the same way, but the email address set up in their account is already entered when they visit a page with an out-of-stock product:
![Registered user subscription](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Mailing+&+Communication/Product+is+Available+Again/registered-user-subscription.png) 

Registered users can change the pre-entered email address to any other one.

Once a customer subscribed, the email address input field is replaced with the **Do not notify me when back in stock** button.
![Do not notify me when back in stock button](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Mailing+&+Communication/Product+is+Available+Again/do-not-notify-button.png) 

An email about a successful subscription is sent to the entered email address:
![Email about successful subscription](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Mailing+&+Communication/Product+is+Available+Again/successful-subscription.png) 

If a customer clicks **Do not notify me when back in stock**, they will receive an email about a successful cancellation of the subscription:
![Cancellation of subscription](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Mailing+&+Communication/Product+is+Available+Again/successful-unsubscription.png) 

Those who subscribed to the newsletter will receive an email once the product is available, no matter how the status of availability becomes positive.
![Product is available](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Mailing+&+Communication/Product+is+Available+Again/product-is-available.png) 

{% info_block infoBox %}
Each email sent as a part of the subscription, contains the unsubscribe from this list button as shown on the screenshot above.
{% endinfo_block %}

Currently, there is no Zed UI for the feature. The newsletter text files are located in `/src/Spryker/Zed/AvailabilityNotification/Presentation/Mail`.

A Back Office user can check the list of subscriptions in the `spy_availability_subscription`database table.

The scheme below illustrates relations between `Availability`, `AvailabilityNotification`, `AvailabilityNotificationWidget` and `ProductDetailPage` modules:
![Module relations scheme](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Mailing+&+Communication/Product+is+Available+Again/module-diagram.png) 

<!-- Last review date: Feb 19, 2019 by Jeremy Foruna, Andrii Tserkovnyi -->