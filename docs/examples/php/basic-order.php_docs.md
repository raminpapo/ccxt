# Documentation: examples/php/basic-order.php

## File Metadata

- **Path**: `examples/php/basic-order.php`
- **Size**: 795 bytes
- **Lines**: 39
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\binance (array(
    'apiKey' => 'YOUR_API_KEY', // change for your keys
    'secret' => 'YOUR_API_SECRET',
));

$message = null;

try {

    $exchange->load_markets();

    $exchange->verbose = true; // uncomment for debugging purposes

    // adjust your values below

    $symbol = 'BTC/USDT';
    $order_type = 'limit';
    $side = 'sell';
    $amount = 0.123; // adjust for your amount
    $price = 50000; // adjust for your price (for limit orders)

    $result = $exchange->create_order ($symbol, $order_type, $side, $amount, $price);
    var_dump ($result);

} catch (Exception $e) {

    echo get_class($e) . ': ' . $e->getMessage() . "\n";
}

?>

```

## High-Level Overview

This is a PHP file located at `examples/php/basic-order.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 23
- Comment lines: 1
- Blank lines: 15

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
php examples/php/basic-order.php
```

