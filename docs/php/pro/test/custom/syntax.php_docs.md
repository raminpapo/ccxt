# Documentation: php/pro/test/custom/syntax.php

## File Metadata

- **Path**: `php/pro/test/custom/syntax.php`
- **Size**: 590 bytes
- **Lines**: 20
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

echo "Checking PHP Syntax...\n";
echo "In case of failure, follow the rules: https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md\n\n";

function on_error ($errno, $message, $file, $line) {
    $message = "$message in $file on line $line";
    throw new ErrorException ($message, $errno);
}

set_error_handler ('on_error');

// this script should be launched from the root of the repo
require_once 'vendor/autoload.php';

foreach (\ccxt\pro\Exchange::$exchanges as $id) {
    $exchange = '\\ccxt\\pro\\' . $id;
    $exchanges[$id] = new $exchange (array ('verbose' => false));
}

```

## High-Level Overview

This is a PHP file located at `php/pro/test/custom/syntax.php`.

**Functions defined**: on_error



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 13
- Comment lines: 1
- Blank lines: 6

### Main Components

**Functions** (1):
- `on_error()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `vendor/autoload.php` (imported)
- `vendor/autoload.php` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
