# GeekMusclay Coding Standards

## Installation

1. Install the module via composer by running:

   ```bash
   composer require --dev geekmusclay/coding-standard
   ```

2. Add composer scripts into your `composer.json`:

   ```json
   "scripts": {
     "cs-check": "phpcs",
     "cs-fix": "phpcbf"
   }
   ```

3. Create file `phpcs.xml` on base path of your repository with this content:

   ```xml
   <?xml version="1.0"?>
   <ruleset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:noNamespaceSchemaLocation="vendor/squizlabs/php_codesniffer/phpcs.xsd">

       <arg name="basepath" value="."/>
       <arg name="cache" value=".phpcs-cache"/>
       <arg name="colors"/>
       <arg name="extensions" value="php"/>
       <arg name="parallel" value="80"/>

       <!-- Show progress -->
       <arg value="p"/>

       <!-- Paths to check -->
       <file>config</file>
       <file>src</file>
       <file>test</file>

       <!-- Include all rules from the Laminas Coding Standard -->
       <rule ref="GeekmuaclayCodingStandard"/>
   </ruleset>
   ```

You can add or exclude some locations in that file.
For a reference please see: https://github.com/squizlabs/PHP_CodeSniffer/wiki/Annotated-Ruleset

## Usage

- To run checks only:

  ```bash
  composer cs-check
  ```

- To automatically fix many CS issues:

  ```bash
  composer cs-fix
  ```

## Ignoring parts of a File

> Note: Before PHP_CodeSniffer version 3.2.0, `// @codingStandardsIgnoreStart` and `// @codingStandardsIgnoreEnd` were
> used. These are deprecated and will be removed in PHP_CodeSniffer version 4.0.