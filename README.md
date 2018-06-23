# TLD Enumerations
Lists of every [IANA TLD](http://data.iana.org/TLD/tlds-alpha-by-domain.txt) in various formats. The lists may be continuously updated using the included [update utility](#updating-the-tld-format-files) that pulls the latest data from IANA.

 * [CSV Format](./tlds.csv)
 * [All Format Files](#tld-list-formats)
 * [Updating the Format Files](#updating-the-tld-format-files)
 * [Node Usage](#node-usage)
 * [PHP Usage](#php-usage)
 
## Usage
Because the lists are provided in universial CSV and JSON formats, they can be easily utilitized in most programming environments.
Additionally, for convenience, some native programming language formats have also been provided.
 * [Node Usage](#node-usage)
 * [More Node Examples](#more-node-examples)
 * [PHP Usage](#php-usage)
 * [More PHP Examples](#more-php-examples)

### Node Usage
 * use npm to add the `tld-enum` package to your project
   ```sh
   $ npm install tld-enum --save
   ```
   
 * add the module to your source
 
   ```js
   const tldEnum = require('tld-enum');
   ```
   
 * access the list by using the `tldEnum.tldList` array
 
   ```js
   const tldEnum = require('tld-enum');
   console.log(tldEnum.list); //an array with every IANA TLD
   ```
   
   The following example...
   ```js
   const tldEnum = require('tld-enum');

   console.log("There are " + tldEnum.list.length + " IANA TLDs");

   let tldCheck;

   tldCheck = "com";
   console.log("Is '" + tldCheck + "' a real TLD?");
   if (tldEnum.list.indexOf(tldCheck.toLowerCase()) != -1) {
       console.log("  yes");
   } else {
       console.log("  no");
   }

   tldCheck = "somethingWeird";
   console.log("Is '" + tldCheck + "' a real TLD?");
   if (tldEnum.list.indexOf(tldCheck.toLowerCase()) != -1) {
       console.log("  yes");
   } else {
       console.log("  no");
   }
   ```
   
   Should produce the following output...
   ```txt
   There are 1577 IANA TLDs
   Is 'com' a real TLD?
      yes
   Is 'somethingWeird' a real TLD?
      no
   ```

#### More Node Examples
 * [js-demo.js](/examples/js-demo.js) Demo using the simple array of every TLD in JavaScript.
 * [js-desc-demo.js](/examples/js-desc-demo.js) Demo using the TLD description hashmap in JavaScript.
 * [js-type-demo.js](/examples/js-type-demo.js) Demo using the TLD type hashmap in JavaScript.
 * [js-info-demo.js](/examples/js-info-demo.js) Demo using the array of TLD info hashmaps in JavaScript.

### PHP Usage
 * use composer to add the `katmore/tld-enum` package to your project
   ```sh
   $ composer require katmore/tld-enum
   ```
   
 * access the list by using the `\TldEnum\TldList::TLD_LIST` class constant array
 
   ```php
   <?php
   print_r(\TldEnum\TldList::TLD_LIST); //an array with every IANA TLD
   ```
 
   The following example...
   ```php
   <?php
   use TldEnum\TldList;

   echo "There are " . count(TldList::TLD_LIST) . " IANA TLDs\n";

   $tldCheck = "com";
   echo "Is '$tldCheck' a real TLD?\n";
   if (in_array(strtolower($tldCheck), TldList::TLD_LIST)) {
       echo "  yes\n";
   } else {
       echo "  no\n";
   }

   $tldCheck = "somethingWeird";
   echo "Is '$tldCheck' a real TLD?\n";
   if (in_array(strtolower($tldCheck), TldList::TLD_LIST)) {
       echo "  yes\n";
   } else {
       echo "  no\n";
   }
   ```
   
   Should produce the following output...
   ```txt
   There are 1577 IANA TLDs
   Is 'com' a real TLD?
      yes
   Is 'somethingWeird' a real TLD?
      no
   ```

#### More PHP Examples
 * [php-demo.php](/examples/php-demo.php) Demo using the simple array of every TLD in PHP.
 * [php-TldDesc-demo.php](/examples/php-TldDesc-demo.php) Demo using the TLD description hashmap in PHP.
 * [php-TldType-demo.php](/examples/php-TldType-demo.php) Demo using the TLD type hashmap in PHP.
 * [php-TldInfo-demo.php](/examples/php-TldInfo-demo.php) Demo using the array of TLD info hashmaps in PHP.

## TLD List Formats
 * **CSV**: [tlds.csv](/tlds.csv)
 
    A CSV file providing a row for every IANA TLD with the following three columns: *domain* (TLD), *description*, and *type*.
    
 * **PHP**
    * [TldList.php](/formats/php/TldEnum/TldList.php)
 
       A PHP source file providing a class constant array comprised of every IANA TLD.
       
    * [TldDesc.php](/formats/php/TldEnum/TldDesc.php)
 
       A PHP source file providing a class constant assoc array with a key for every IANA TLD and the corresponding TLD's "description" as the value.
       
    * [TldType.php](/formats/php/TldEnum/TldType.php)
 
       A PHP source file providing a class constant assoc array with a key for every IANA TLD and the corresponding TLD's "type" as the value.
       
    * [TldInfo.php](/formats/php/TldEnum/TldInfo.php)
 
       A PHP source file providing a class constant array of "info" assoc array elements of every IANA TLD.
  
 * **JSON**
    * [tld-list.json](/formats/json/tld-list.json)
 
       A JSON formatted array comprised of every IANA TLD.
       
    * [tld-desc.json](/formats/json/tld-desc.json)
 
       A JSON formatted object with a property for every IANA TLD and the corresponding TLD's "description" as the value.
       
    * [tld-type.json](/formats/json/tld-type.json)
 
       A JSON formatted object with a property for every IANA TLD and the corresponding TLD's "type" as the value.
       
    * [tld-info.json](/formats/json/tld-info.json)
 
       A JSON formatted array of "info" object elements of every IANA TLD.
       
 * **JavaScript**
    * [list.js](/formats/js/tld-enum/list.js)
 
       An export module with an array comprised of every IANA TLD.
       
    * [desc.js](/formats/js/tld-enum/desc.js)
 
       An export module with an object containing a property for every IANA TLD and the corresponding TLD's "description" as the value.
       
    * [type.js](/formats/js/tld-enum/type.js)
 
       An export module with an object containing a property for every IANA TLD and the corresponding TLD's "type" as the value.
       
    * [info.js](/formats/js/tld-enum/info.js)
 
       An export module with an array comprised of "info" object elements of every IANA TLD.
    
## Updating the TLD format files
All [TLD List Formats](#tld-list-formats) can be updated with the latest data from IANA by using the [**TLD Update Utility**](/bin/devel/update-formats.sh).

```sh
$ bin/devel/update-formats.sh
```

### TLD Update Utility Prerequisites
 * Node.js version 8.11 or higher.
 * (Optional) PHP command-line version 7.2 or higher, to re-generate the [PHP format files](#tld-list-formats).
 * The *devDependencies* from [*package.json*](./package.json) must be available.
   
   * If **tld-enum** was installed in an outside project using npm, then the *tld-enum* dev dependencies must be installed manually, as in the following example:
   
     ```sh
     npm install async-request --save-dev
     npm install cheerio --save-dev
     npm install commander --save-dev
     npm install country-data --save-dev
     npm install countryjs --save-dev
     npm install csv-parse --save-dev
     npm install csv-stringify --save-dev
     npm install es6-promisify --save-dev
     npm install fs --save-dev
     npm install fs-extra --save-dev
     npm install md5-file --save-dev
     npm install pathinfo --save-dev
     npm install request --save-dev
     npm install tmp --save-dev
     ```
     
   * If **tld-enum** was installed in an outside project using npm, then the **TLD Update Utility** can be executed from the *node_module* directory, as in the following example:
      
     ```sh
     node_modules/tld-enum/bin/devel/update-formats.sh
     ```

### TLD Update Utility Usage
```txt
usage:
  update-formats.sh [-h]|[-q][format file options...]

-h,--help: Print a help message and exit.
-q,--quiet: Print only critical messages.

format file options:
  --force-php: Creating the PHP format files is mandatory.
  --skip-php: Always skip creating the PHP format files.
  --skip-csv: Use existing tlds.csv and do not download new data from IANA.
```

### TLD Update Helpers
Internally, the *TLD Update Utility* uses multiple *"helper" scripts* to generate the full set of native format lists.
These individual *"helper" scripts* should not be directly executed except for development and troubleshooting purposes.

## Legal
The source code in this project is based on a fork of certain source code originally from the [incognico/list-of-top-level-domains](https://github.com/incognico/list-of-top-level-domains) project, as retrieved on 2017-12-04, which was published to the public domain.

### Copyright
TLD Enumerations - https://github.com/katmore/tld-enum

The following copyright notice applies to all resources in this project unless specifically noted otherwise:

Copyright (c) 2017-2018 Doug Bird. All Rights Reserved.

### License
All resources in the *TLD Enumerations* project are copyrighted free software unless specifically noted otherwise.

You may redistribute and modify it under either the terms and conditions of the
"The MIT License (MIT)"; or the terms and conditions of the "GPL v3 License".
See [LICENSE](/LICENSE) and [GPLv3](/GPLv3).

These licensing conditions do not apply to any resources that have been released into the public domain; which are listed in the [**"Public Domain Resources"**](/README.md#public-domain-resources) section of the *TLD Enumerations* project's [README](/README.md) document.

### Public Domain Resources
The following resources of this project are hereby released into the public domain:
 * [tlds.csv](/tlds.csv)
 * [formats/js/tld-enum/list.js](/formats/js/tld-enum/list.js)
 * [formats/js/tld-enum/desc.js](/formats/js/tld-enum/desc.js)
 * [formats/js/tld-enum/info.js](/formats/js/tld-enum/info.js)
 * [formats/js/tld-enum/type.js](/formats/js/tld-enum/type.js)
 * [formats/json/tld-list.json](/formats/json/tld-list.json)
 * [formats/json/tld-desc.json](/formats/json/tld-desc.json)
 * [formats/json/tld-info.json](/formats/json/tld-info.json)
 * [formats/json/tld-type.json](/formats/json/tld-type.json)
 * [formats/php/TldEnum/TldList.php](/formats/php/TldEnum/TldList.php)
 * [formats/php/TldEnum/TldDesc.php](/formats/php/TldEnum/TldDesc.php)
 * [formats/php/TldEnum/TldInfo.php](/formats/php/TldEnum/TldInfo.php)
 * [formats/php/TldEnum/TldType.php](/formats/php/TldEnum/TldType.php)
 * [assets/tld-desc.csv](/assets/tld-desc.csv)
