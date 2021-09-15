---
title: FACT-Finder - Exporting CSVs
description: Export data to FACT-Finder CSV by applying the configuration.
originalLink: https://documentation.spryker.com/v6/docs/search-factfinder-export-csv
originalArticleId: 90e10bd1-2e8c-4f05-8eba-223253ff2cee
redirect_from:
  - /v6/docs/search-factfinder-export-csv
  - /v6/docs/en/search-factfinder-export-csv
---

## Output Folder

Define an output folder where  the CSV files will be generated by adding the following line in your configuration file:
```php
<?php
$config[FactFinderSdkConstants::CSV_DIRECTORY] = APPLICATION_ROOT_DIR . '/path/to/generated/csv/files';
```

Zed must have Read / Write access to this folder because  we will generate and read CSV files in that directory.

## Queries

To export data to the CSV, we need to define the queries  executed in the database.

All queries are located in the `SprykerEco\Zed\FactFinderSdk\Persistence\FactFinderSdkQueryContainer ` directory.

To change the query in `FactFinderSdk` module, we need to extend the `FactFinderSdkQueryContainer` in your project.

## How is my Query Mapped to CSV Output ?

If you need to modify the CSV column mapping for any reason, you will have to extend the `FactFinderSdkQueryContainer` from `FactFinderSdk` module and implement your own `addColumns` method.

### Console

To export the products and categories using the queries we made before, we must register the `FactFinderSdk` console command in [Console](/docs/scos/dev/back-end-development/{{site.version}}/console-commandsconsole-commands-in-spryker.html).

The `FactFinderSdk` module already includes everything though you will need to add `FactFinderSdkExportConsole` to `Pyz\Zed\Console\ConsoleDependencyProvider` like below:
```php
<?php

/**
* @param \Spryker\Zed\Kernel\Container $container
*
* @return \Symfony\Component\Console\Command\Command[]
*/
public function getConsoleCommands(Container $container)
{
 $commands = [
 ...
 new FactFinderSdkExportConsole(),
 ];
 ...
}
```

### Restrictions

* The first row of the CSV file must contain the field names. The structure of this row is identical to the data rows.
* The number of fields is limited to 128. However, the standard FACT-Finder modules require the use of a limited number of fields. For that reason, we recommend that you do not use this limit in full. If your product database contains more than 128 attributes, you can store them in the multi-attribute fields.
* The field content is not limited in length. There is, however, a limit on the complete data record size. This limit is set at 50,000 characters. In special cases, the limit can be removed. We consider it as a part of a special FACT-Finder package creation process we perform  for you.

### Recommendations

* To save transmission bandwidth, you may compress the file in ZIP format before sending it to FACT-Finder. Other compression formats are also supported: GZip, BZip, GZip+TAR. RAR files and other archive formats are not supported by FACT-Finder automatic data update process.
* FACT-Finder suggests two ways of data exporting - downloads and uploads. Currently, export implemented for the downloads.
You need to create an URL for a CSV file or put it into a public folder. Then you can set up an URL and an interval  in a FACT-Finder channel management panel to download the CSV file.
* A CSV file export can be scheduled with the help of a cron job or triggered by an event.
*  If additional attributes are available, they can also be used by the search process.
* If you have attribute types that vary from item to item, it does not make sense to create a separate field for every possible attribute type. Instead, you can create an attribute field that is formatted according to the following pattern: `|attribute1=value|attribute2=value|attribute3=value|`.Please note that  for the Attribute field the pipe separator `(|)` appears between the attributes, as well as at the beginning and at the end of the field contents. Also note, that the symbols `|`, `#` and `=` are reserved symbols in attribute field data and therefore are not permitted here. For some attributes, it is desirable to include a unit or currency designator. You must separate the attribute name from the unit with a double tilde `(~~)`. Please note that there can only be one unit per attribute name (even if the attributes appear in different data records), so the values must be normalized beforehand.

## Checking Your Setup

If all the steps were correct you should be able to see the `fact-finder:export:products` command in the FACT-Finder section when you run `vendor/bin/console` from the project's root folder.

Running `vendor/bin/console fact-finder:export:products` will create several CSV files (one per locale) in the folder you specified in
```
$config[FactFinderSdkConstants::CSV_DIRECTORY]
```