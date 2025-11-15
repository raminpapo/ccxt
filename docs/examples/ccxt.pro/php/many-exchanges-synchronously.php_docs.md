# Documentation: examples/ccxt.pro/php/many-exchanges-synchronously.php

## File Metadata

- **Path**: `examples/ccxt.pro/php/many-exchanges-synchronously.php`
- **Size**: 758 bytes
- **Lines**: 28
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(dirname(__FILE__))));
include $root . '/ccxt.php';


$config = array('enableRateLimit' => true);
$binance = new \ccxt\pro\binance($config);
$bittrex = new \ccxt\pro\bittrex($config);
$symbol = "BTC/USDT";

$loop = function($exchange, $symbol) {
    echo 'got inside' . PHP_EOL;
    for ($i = 0; $i < 5; $i++) {
        $ticker = yield $exchange->watch_ticker($symbol);
        print_ticker($ticker, $exchange->id, $symbol);
    }
};

function print_ticker($ticker, $exchange_name, $symbol) {
    $bid = $ticker['bid'];
    $ask = $ticker['ask'];
    echo "$exchange_name $symbol - bid: $bid <> ask: $ask" . PHP_EOL;
}

\React\Async\coroutine($loop, $bittrex, $symbol);
\React\Async\coroutine($loop, $binance, $symbol);

```

## High-Level Overview

This is a PHP file located at `examples/ccxt.pro/php/many-exchanges-synchronously.php`.

**Functions defined**: print_ticker



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 21
- Comment lines: 0
- Blank lines: 7

### Main Components

**Functions** (1):
- `print_ticker()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/ccxt.pro/php/many-exchanges-synchronously.php
```

