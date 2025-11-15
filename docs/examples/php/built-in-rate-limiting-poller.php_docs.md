# Documentation: examples/php/built-in-rate-limiting-poller.php

## File Metadata

- **Path**: `examples/php/built-in-rate-limiting-poller.php`
- **Size**: 577 bytes
- **Lines**: 21
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = '\\ccxt\\poloniex';
$exchange = new $exchange();

$symbol = 'DOGE/BTC';

while (true) {
    $order_book = $exchange->fetch_order_book($symbol);
    echo "----------------------------------------------------------------\n";
    echo date('c') . "\n";
    echo count($order_book['bids']) . " bids and " . count($order_book['asks']) . " asks\n";
    echo sprintf("bid: %.8f ask: %.8f", $order_book['bids'][0][0], $order_book['asks'][0][0]) . "\n";
}

```

## High-Level Overview

This is a PHP file located at `examples/php/built-in-rate-limiting-poller.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 14
- Comment lines: 0
- Blank lines: 7

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
php examples/php/built-in-rate-limiting-poller.php
```

