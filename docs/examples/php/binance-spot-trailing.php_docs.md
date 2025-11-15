# Documentation: examples/php/binance-spot-trailing.php

## File Metadata

- **Path**: `examples/php/binance-spot-trailing.php`
- **Size**: 2,120 bytes
- **Lines**: 76
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

echo 'CCXT v' . \ccxt\Exchange::VERSION . "\n";

$exchange = new \ccxt\binance(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET_KEY',
    // 'verbose' => true, // uncomment if debug output is needed
));

// You can read more about spot trailing orders here:
// https://github.com/binance/binance-spot-api-docs/blob/master/faqs/trailing-stop-faq.md

// Example 1: Spot : trailing spot loss
function example_1($exchange) {
    $markets = $exchange->load_markets(true);

    // create STOP_LOSS_LIMIT BUY with a trailing stop of 5%.
    $symbol = 'LTC/USDT';
    $type = 'STOP_LOSS_LIMIT';
    $side = 'buy';
    $amount = 0.4;
    $price = 25;
    $params = array(
        'trailingDelta' => 500, // 5% in BIPS
    );
    $create_order = $exchange->create_order($symbol, $type, $side, $amount, $price, $params);
    
    print_r('Create order id:' . $create_order['id']);
    
    // cancel created order
    $canceled_order = $exchange->cancel_order($create_order['id'] . $symbol);
    print_r ($canceled_order);
}

// -----------------------------------------------------------------------------------------

// Example 2: Spot : TAKE_PROFIT_LIMIT BUY order
function example_2($exchange) {
    $markets = $exchange->load_markets(true);

    // create STOP_LOSS_LIMIT BUY with a trailing stop of 5%.
    $symbol = 'LTC/USDT';
    $type = 'TAKE_PROFIT_LIMIT';
    $side = 'buy';
    $amount = 0.2;
    $price = 70;
    $params = array(
        'trailingDelta' => 250, // 2.5% in BIPS
    );

    $create_order = $exchange->create_order($symbol, $type, $side, $amount, $price, $params);
    
    print_r('Create order id:' . $create_order['id']);
    
    // cancel created order
    $canceled_order = $exchange->cancel_order($create_order['id'], $symbol);
    print_r ($canceled_order);
}
// -----------------------------------------------------------------------------------------

function main($exchange) {
    example_1($exchange);
    example_2($exchange);
}

main($exchange)

?>

```

## High-Level Overview

This is a PHP file located at `examples/php/binance-spot-trailing.php`.

**Functions defined**: main, example_1, example_2



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 45
- Comment lines: 11
- Blank lines: 20

### Main Components

**Functions** (3):
- `example_1()`
- `example_2()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/binance-spot-trailing.php
```

