# Documentation: examples/php/bitfinex2-fetch-ohlcv-since-limit.php

## File Metadata

- **Path**: `examples/php/bitfinex2-fetch-ohlcv-since-limit.php`
- **Size**: 925 bytes
- **Lines**: 29
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

// instantiate the exchange by id
$exchange = '\\ccxt\\bitfinex2';
$exchange = new $exchange();

// load all markets from the exchange
$markets = $exchange->load_markets();

function run($exchange, $symbol, $timeframe, $since, $limit) {
    $ohlcvs = $exchange->fetch_ohlcv($symbol, $timeframe, $since, $limit);
    foreach ($ohlcvs as $v) {
        printf ("%s O:%.8f H:%.8f L:%.8f C:%.8f V:%.8f\n", $exchange->iso8601($v[0]), $v[1], $v[2], $v[3], $v[4], $v[5]);
    }
}

printf("--------------------------------------------------------------\n");
run($exchange, 'ETH/BTC', '1m', 1518842513569, 5);
printf("--------------------------------------------------------------\n");
run($exchange, 'ETH/BTC', '1m', 1518842513569, 10);
printf("--------------------------------------------------------------\n");

?>
```

## High-Level Overview

This is a PHP file located at `examples/php/bitfinex2-fetch-ohlcv-since-limit.php`.

**Functions defined**: run



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 19
- Comment lines: 2
- Blank lines: 8

### Main Components

**Functions** (1):
- `run()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/bitfinex2-fetch-ohlcv-since-limit.php
```

