# Documentation: examples/php/async-await-fetch.php

## File Metadata

- **Path**: `examples/php/async-await-fetch.php`
- **Size**: 1,978 bytes
- **Lines**: 59
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
// Instead of yield generators, now users can use modern Async/Await syntax
include dirname(dirname(dirname(__FILE__))) . '/ccxt.php';
use function React\Async\async;
use function React\Async\await;
date_default_timezone_set('UTC');

$exchange = new ccxt\async\binance([]);
await($exchange->load_markets());
$symbols = array('BTC/USDT', 'ETH/USDT');


// ###########################################
echo "########## Individual await ##########\n";
foreach ($symbols as $symbol) {
    $ticker = await($exchange->fetch_ticker($symbol));
    echo "{$ticker['symbol']} {$ticker['close']}\n";
}
// ###########################################


// ###########################################
echo "########### Combined await ###########\n";
$promises = [];
foreach ($symbols as $symbol) {
    $promises[] = $exchange->fetch_ticker($symbol);
}
$tickers = await(React\Promise\all($promises));
echo "{$tickers[0]['symbol']} {$tickers[0]['close']}  |  {$tickers[1]['symbol']} {$tickers[1]['close']}\n";
// ###########################################



// ###########################################
$exchange->fetch_ticker($symbols[0])->then(function($ticker){
    echo "########## Callback->then ##########\n";
    echo "{$ticker['symbol']} {$ticker['close']}\n";
});
// ###########################################



// ################### custom async function ########################
function myFunc ($exchange, $symbol) {
    return async(function () use ($exchange, $symbol) {
        try {
            // example sleep
            await(React\Promise\Timer\sleep(0.5));
            $ticker = await($exchange->fetch_ticker($symbol));
            echo "########## Custom async function ##########\n";
            echo "{$ticker['symbol']} {$ticker['close']}\n";
        } catch (\ccxt\NetworkError $e) {
            echo '[Network Error] ' . $e->getMessage() . "\n";
        }
    });
}
await(myFunc($exchange, $symbols[0])());
// ###########################################

```

## High-Level Overview

This is a PHP file located at `examples/php/async-await-fetch.php`.

**Functions defined**: myFunc, React



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 37
- Comment lines: 10
- Blank lines: 12

### Main Components

**Functions** (2):
- `React()`
- `myFunc()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/async-await-fetch.php
```

