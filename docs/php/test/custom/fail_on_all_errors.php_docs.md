# Documentation: php/test/custom/fail_on_all_errors.php

## File Metadata

- **Path**: `php/test/custom/fail_on_all_errors.php`
- **Size**: 621 bytes
- **Lines**: 23
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace ccxt;
include_once (__DIR__.'/../../../ccxt.php');

// ----------------------------------------------------------------------------

function fail_on_all_errors($errno, $errstr, $errfile, $errline) {

    if (!(error_reporting() & $errno)) {
        // This error code is not included in error_reporting, so let it fall
        // through to the standard PHP error handler
        return false;
    }

    echo "Error [$errno] $errstr on line $errline in file $errfile\n";
    exit(1);

    /* Don't execute PHP internal error handler */
    return true;
}

set_error_handler('ccxt\\fail_on_all_errors');

```

## High-Level Overview

This is a PHP file located at `php/test/custom/fail_on_all_errors.php`.

**Functions defined**: fail_on_all_errors

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 13
- Comment lines: 4
- Blank lines: 6

### Main Components

**Functions** (1):
- `fail_on_all_errors()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/../../../ccxt.php` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
