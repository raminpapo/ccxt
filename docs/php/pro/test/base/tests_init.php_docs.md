# Documentation: php/pro/test/base/tests_init.php

## File Metadata

- **Path**: `php/pro/test/base/tests_init.php`
- **Size**: 381 bytes
- **Lines**: 17
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace ccxt\pro;
include_once (__DIR__.'/../../../../ccxt.php');
// ----------------------------------------------------------------------------



include_once (__DIR__.'/test_order_book.php');
include_once (__DIR__.'/test_cache.php');
// todo : include_once (__DIR__.'/test_close.php');


function base_tests_init_ws() {
    test_ws_order_book();
    test_ws_cache();
}

```

## High-Level Overview

This is a PHP file located at `php/pro/test/base/tests_init.php`.

**Functions defined**: base_tests_init_ws



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 9
- Comment lines: 2
- Blank lines: 6

### Main Components

**Functions** (1):
- `base_tests_init_ws()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `/test_order_book.php` (referenced)
- `/test_close.php` (referenced)
- `/../../../../ccxt.php` (referenced)
- `/test_cache.php` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
