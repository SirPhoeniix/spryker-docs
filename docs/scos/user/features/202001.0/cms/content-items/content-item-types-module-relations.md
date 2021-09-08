---
title: Content Item Types- Module Relations
description: Learn about all the content item types and module relations used for them.
originalLink: https://documentation.spryker.com/v4/docs/content-item-types-module-relations
originalArticleId: 009ad7da-7319-4363-8f7e-a5cdb0dba24d
redirect_from:
  - /v4/docs/content-item-types-module-relations
  - /v4/docs/en/content-item-types-module-relations
---

This document describes each content item type and the modules relations used for them.

## Banner
Banner content item is a content piece that consists of text, a background image and a link. A content manager specifies the values when [creating the content item](/docs/scos/user/user-guides/202001.0/back-office-user-guide/content-management/content-items/creating-content-items.html#content-item--banner) in the Back Office > **Content Management** > **Content Items**. 
The scheme shows the module relations of the Banner content item:
![Banner CI module relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/CMS/Content+Items/Content+Items+Types%3A+Module+Relations/banner-module-relations.png) 

### Banner API
A developer can fetch the content item data via API. Also, they can view the content item details for a specific locale. 

The scheme below shows the Banner API module relations:
![Banner API module relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/CMS/Content+Items/Content+Items+Types%3A+Module+Relations/banner-api-module-relations.png) 

### Banner Data Importer
A developer can create and edit the content items by importing them.

The scheme below shows the module relations of the content item data importers:
![Banner Content Item Data Importers module relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/CMS/Content+Items/Content+Items+Types%3A+Module+Relations/banner-data-importers-module-relations.png) 


See [Data Importers Overview and Implementation](/docs/scos/dev/developer-guides/202001.0/development-guide/back-end/data-manipulation/data-ingestion/data-importers/data-importers-overview-and-implementation.html) for more details.
***
## Abstract Product List 
Abstract product list content item is a content piece that consists of text and [abstract products](/docs/scos/dev/features/202001.0/product-information-management/product-abstraction.html). A content manager selects existing abstract products when [creating the content item](/docs/scos/user/user-guides/202001.0/back-office-user-guide/content-management/content-items/creating-content-items.html#content-item--abstract-product-list) in the Back Office > **Content Management** > **Content Items**. 
The scheme below shows the module relations of the Abstract product list content item and its components:
* data importer
* API

![Abstract Product List module relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/CMS/Content+Items/Content+Items+Types%3A+Module+Relations/abstract-product-list-module-relations.png) 

### Abstract Product List Data Importer
A developer can create and update the content items by importing them.

See [Data Importers Overview and Implementation](/docs/scos/dev/developer-guides/202001.0/development-guide/back-end/data-manipulation/data-ingestion/data-importers/data-importers-overview-and-implementation.html) for more details.

### Abstract Product List API
A developer can fetch the information on each abstract product included into a contnet item via API based on the content item key. Also, they can view details of content items for all or a specific locale. 

***
## Product Set 
Product set content item is a content piece that consists of text and a [product set](/docs/scos/dev/features/202001.0/product-information-management/product-set.html). A content manager selects an existing product set when [creating the content item](/docs/scos/user/user-guides/202001.0/back-office-user-guide/content-management/content-items/creating-content-items.html#content-item--product-set) in the Back Office > **Content Management** > **Content Items**. 
The scheme below shows the module relations of the Product set content item and its importer:
![Product Set content item module relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/CMS/Content+Items/Content+Items+Types%3A+Module+Relations/product-set-module-relations.png) 

### Product Set Data Importer
Developers can create and update the content items by importing them.

See [Data Importers Overview and Implementation](/docs/scos/dev/developer-guides/202001.0/development-guide/back-end/data-manipulation/data-ingestion/data-importers/data-importers-overview-and-implementation.html) for more details.

***
## File List 
File list content item is a content piece that consists of text and a clickable link or icon to download a file. A content manager selects existing files when [creating the content item](/docs/scos/user/user-guides/202001.0/back-office-user-guide/content-management/content-items/creating-content-items.html#content-item--file-list) in the Back Office > **Content Management** > **Content Items**. 

The scheme below shows the module relations of the File list content item:
![File List module relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/CMS/Content+Items/Content+Items+Types%3A+Module+Relations/file-list-module-relations.png) 