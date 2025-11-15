# Documentation: php/test/custom/syntax.php

## File Metadata

- **Path**: `php/test/custom/syntax.php`
- **Size**: 510 bytes
- **Lines**: 19
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

include_once 'ccxt.php';

foreach (\ccxt\Exchange::$exchanges as $id) {
    $exchange = '\\ccxt\\' . $id;
    $exchanges[$id] = new $exchange (array ('verbose' => false));
}

```

## High-Level Overview

This is a PHP file located at `php/test/custom/syntax.php`.

**Functions defined**: on_error



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 13
- Comment lines: 0
- Blank lines: 6

### Main Components

**Functions** (1):
- `on_error()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
