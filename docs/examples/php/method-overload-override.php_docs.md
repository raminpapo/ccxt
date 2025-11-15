# Documentation: examples/php/method-overload-override.php

## File Metadata

- **Path**: `examples/php/method-overload-override.php`
- **Size**: 1,046 bytes
- **Lines**: 33
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace ccxt;
include_once (__DIR__.'/../../ccxt.php');

error_reporting(E_ALL);
date_default_timezone_set('UTC');
// -----------------------------------------------------------------------------

// ###############################################
// ####### APPROACH 1: Overload the method #######
// ###############################################
function example_1() {
    $ex = new \ccxt\kucoin();
    $ex->add_method('fetch_ticker', function($symbol, $params = []) {
        return 'hello from the overload method';
    });
    var_dump($ex->call_method('fetch_ticker', ['BTC/USDT']));
}
example_1();


// ###############################################
// ####### APPROACH 2: extend the class    #######
// ###############################################
function example_2() {
    $ex = new class extends \ccxt\kucoin {
        public function fetch_ticker($symbol, $params = []) {
            return 'Hello from the anonymous class!';
        }
    };
    var_dump($ex->fetch_ticker('fetch_ticker', ['BTC/USDT']));
}
example_2();
```

## High-Level Overview

This is a PHP file located at `examples/php/method-overload-override.php`.

**Classes defined**: extends

**Functions defined**: example_1, fetch_ticker, example_2



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 22
- Comment lines: 7
- Blank lines: 4

### Main Components

**Functions** (3):
- `example_1()`
- `example_2()`
- `fetch_ticker()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/../../ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/method-overload-override.php
```

