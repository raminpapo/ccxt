# Documentation: examples/php/binance-set-futures-leverage.php

## File Metadata

- **Path**: `examples/php/binance-set-futures-leverage.php`
- **Size**: 1,006 bytes
- **Lines**: 38
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

// https://github.com/ccxt/ccxt/wiki/Manual#instantiation

date_default_timezone_set('UTC');

$exchange_id = 'binance';
$exchange_class = "\\ccxt\\$exchange_id";
$exchange = new $exchange_class(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET',
    'options' => array(
        'defaultType' => 'future'
    ),
));

$exchange->load_markets(); // https://github.com/ccxt/ccxt/wiki/Manual#loading-markets

// $exchange->verbose = true; // verbose mode on, uncomment for debugging

$symbol = 'BTC/USDT';

$market = $exchange->market($symbol);

// https://github.com/ccxt/ccxt/wiki/Manual#passing-parameters-to-api-methods
$params = array(
    'symbol' => $market['id'], // convert a unified CCXT symbol to an exchange-specific market id
    'leverage' => 10,
);

// https://github.com/ccxt/ccxt/wiki/Manual#implicit-api-methods
$response = $exchange->fapiPrivate_post_leverage($params);

print_r ($response);
```

## High-Level Overview

This is a PHP file located at `examples/php/binance-set-futures-leverage.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 22
- Comment lines: 4
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/binance-set-futures-leverage.php
```

