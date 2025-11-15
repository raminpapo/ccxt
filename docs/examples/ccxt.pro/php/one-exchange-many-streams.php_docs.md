# Documentation: examples/ccxt.pro/php/one-exchange-many-streams.php

## File Metadata

- **Path**: `examples/ccxt.pro/php/one-exchange-many-streams.php`
- **Size**: 884 bytes
- **Lines**: 31
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(dirname(__FILE__))));
include $root . '/ccxt.php';

$id = 'aax';
$exchange_class = '\\ccxt\\pro\\' . $id;
$exchange = new $exchange_class(array(
    'enableRateLimit' => true,
));

$symbols = array('BTC/USDT', 'ETH/USDT', 'ETH/BTC');

function print_orderbook($orderbook, $symbol) {
    $id = isset($orderbook['nonce']) ? $orderbook['nonce'] : $orderbook['datetime'];
    echo $id, ' ', $symbol, ' ',
        count($orderbook['asks']), ' asks ', json_encode($orderbook['asks'][0]), ' ',
        count($orderbook['bids']), ' bids ', json_encode($orderbook['bids'][0]), "\n";
}

$loop = function($exchange, $symbol) {
    while (true) {
        $orderbook = yield $exchange->watch_order_book($symbol);
        print_orderbook($orderbook, $symbol);
    }
};

foreach ($symbols as $symbol) {
    \React\Async\coroutine($loop, $exchange, $symbol);
}

```

## High-Level Overview

This is a PHP file located at `examples/ccxt.pro/php/one-exchange-many-streams.php`.

**Functions defined**: print_orderbook



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 24
- Comment lines: 0
- Blank lines: 7

### Main Components

**Functions** (1):
- `print_orderbook()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/ccxt.pro/php/one-exchange-many-streams.php
```

