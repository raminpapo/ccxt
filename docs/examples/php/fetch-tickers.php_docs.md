# Documentation: examples/php/fetch-tickers.php

## File Metadata

- **Path**: `examples/php/fetch-tickers.php`
- **Size**: 1,729 bytes
- **Lines**: 41
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
// ##########################################
// for asynchronous (async/await) version check: https://github.com/ccxt/ccxt/blob/master/examples/php/async-await.php
// ##########################################

include dirname(dirname(dirname(__FILE__))) . '/ccxt.php';
date_default_timezone_set('UTC');

$exchange =new \ccxt\binance(array(
    // 'verbose' => true, // for debugging
    'timeout' => 30000,
));

$markets = $exchange->load_markets();

try {
    if ($exchange->has['fetchTickers']) {
        // one API call for all tickers (preferred way)
        $result = $exchange->fetch_tickers (); // note, don't call it for specifically binance more than once in every few seconds.
        echo "Called fetchTickers() for all tickers at once. Results count: " . count($result) . "\n";
    } else if ($exchange->has['fetchTicker']) {
        // Individual API calls for all tickers one by one (non-preferred way)
        echo "fetchTickers() is not supported by " . $exchange->id . ", calling individual fetchTicker() for each symbol instead.\n";
        // fetch one by one (not recommended)
        $i = 0;
        $test_symbols_amount = 4;
        foreach ($markets as $symbol => $m) {
            if ($i++ && $i > $test_symbols_amount) {
                echo "Stopping after getting " . $test_symbols_amount . " test symbols.\n";
                break;
            }
            $result = $exchange->fetch_ticker($symbol);
            echo "Fetched ticker for " . $result['symbol'] . ", 24hr high: " . $result['high'] . "\n";
        }
    } else {
        echo "fetchTicker/s() not supported by " . $exchange->id . ", skipping.\n";
    }
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}

```

## High-Level Overview

This is a PHP file located at `examples/php/fetch-tickers.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 29
- Comment lines: 7
- Blank lines: 5

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
php examples/php/fetch-tickers.php
```

