# Documentation: php/test/tests_init.php

## File Metadata

- **Path**: `php/test/tests_init.php`
- **Size**: 1,023 bytes
- **Lines**: 38
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt;
use Exception; // a common import
require_once (__DIR__ . '/tests_helpers.php');


$isWs = get_cli_arg_value ('--ws');
$isBaseTests = get_cli_arg_value ('--baseTests');
$runAll = get_cli_arg_value ('--all'); // if neither was chosen


// ####### base tests #######
if ($isBaseTests) {
    if ($isWs) {
        require_once (__DIR__ . '/../pro/test/base/tests_init.php');
        \ccxt\pro\base_tests_init_ws();
        print('base WS tests passed!');
    } else {
        // test base things
        require_once (__DIR__ . '/base/tests_init.php');
        base_tests_init();
        print('base REST tests passed!');
    }
    if (!$runAll) {
        exit(0);
    }
}

// ####### exchange tests #######
if (IS_SYNCHRONOUS) {
    require_once __DIR__ . '/tests_sync.php';
    (new testMainClass ())->init($argvExchange, $argvSymbol, $argvMethod);
} else {
    require_once __DIR__ . '/tests_async.php';
    \React\Async\await((new testMainClass ())->init($argvExchange, $argvSymbol, $argvMethod));
}

```

## High-Level Overview

This is a PHP file located at `php/test/tests_init.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 28
- Comment lines: 3
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/tests_sync.php` (referenced)
- `/tests_helpers.php` (referenced)
- `/tests_async.php` (referenced)
- `/base/tests_init.php` (referenced)
- `/../pro/test/base/tests_init.php` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
