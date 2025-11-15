# Documentation: examples/php/huobi-swaps.php

## File Metadata

- **Path**: `examples/php/huobi-swaps.php`
- **Size**: 1,058 bytes
- **Lines**: 45
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\huobipro(array(
    'apiKey' => 'YOUR_API_KEY', // ←------------ replace with your keys
    'secret' => 'YOUR_SECRET_KEY',
    // 'verbose' => true, // uncomment if debug output is needed
));

try {

    $markets = $exchange->load_markets ();

    // creating a linear swap (limit) order
    $symbol = 'ADA/USDT:USDT';
    $order_type = 'limit';
    $side = 'buy';
    $offset = 'open';
    $leverage = 1;
    $amount = 1;
    $price = 1;

    $params = array (
        'offset' => $offset,
        'lever_rate' => $leverage,
    );

    $order = $exchange->create_order ($symbol, $order_type, $side, $amount, $price, $params);
    var_dump ($order['id']);

} catch (\ccxt\NetworkError $e) {
    echo '[Network Error] ' . $e->getMessage() . "\n";
} catch (\ccxt\ExchangeError $e) {
    echo '[Exchange Error] ' . $e->getMessage() . "\n";
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}

?>

```

## High-Level Overview

This is a PHP file located at `examples/php/huobi-swaps.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 31
- Comment lines: 2
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
php examples/php/huobi-swaps.php
```

