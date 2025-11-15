# Documentation: examples/php/indodax-fetch-balance-create-order-cancel-order.php

## File Metadata

- **Path**: `examples/php/indodax-fetch-balance-create-order-cancel-order.php`
- **Size**: 1,765 bytes
- **Lines**: 65
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\indodax(array(
    'apiKey' => 'YOUR_API_KEY', // ←------------ replace with your keys
    'secret' => 'YOUR_SECRET',
));

//-----------------------------------------------------------------------------
// querying balance

$balance = $exchange->fetch_balance();

print_r($balance);

// do whatever you need here with your balance...

//-----------------------------------------------------------------------------
// placing and canceling orders

$symbol = 'BTC/IDR'; // bitcoin contract according to bitmex futures coding
$type = 'limit';
$side = 'sell'; // or 'buy'
$amount = 1.0;
$price = 6500.0; // or None

// extra params and overrides if necessary
$params = array(
    // ...
);

// buying

$buy_order1 = $exchange->create_limit_buy_order($symbol, $amount, $price, $params);
echo "Buy order 1:\n";
print_r($buy_order1);

$buy_order2 = $exchange->create_order($symbol, $type, 'buy', $amount, $price, $params);
//                             order side hardcoded here ↑ for example
echo "Buy order 2:\n";
print_r($buy_order2);

// selling

$sell_order1 = $exchange->create_limit_sell_order($symbol, $amount, $price, $params);
echo "Sell order 1:\n";
print_r($sell_order1);

$sell_order2 = $exchange->create_order ($symbol, $type, $side, $amount, $price, $params);
//                         order side from a variable here ↑ for example
echo "Sell order 2:\n";
print_r($sell_order2);

// canceling

$exchange->cancel_order($buy_order1['id'], $symbol);
$exchange->cancel_order($buy_order2['id'], $symbol);
$exchange->cancel_order($sell_order1['id'], $symbol);
$exchange->cancel_order($sell_order2['id'], $symbol);

```

## High-Level Overview

This is a PHP file located at `examples/php/indodax-fetch-balance-create-order-cancel-order.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 33
- Comment lines: 12
- Blank lines: 20

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
php examples/php/indodax-fetch-balance-create-order-cancel-order.php
```

