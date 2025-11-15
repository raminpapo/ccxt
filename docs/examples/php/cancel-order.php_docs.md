# Documentation: examples/php/cancel-order.php

## File Metadata

- **Path**: `examples/php/cancel-order.php`
- **Size**: 1,146 bytes
- **Lines**: 36
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
include dirname(dirname(dirname(__FILE__))) . '/ccxt.php';
date_default_timezone_set('UTC');

$exchange = new \ccxt\binance(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET',
    // 'verbose' => true,
));

try {

    $symbol = 'XRP/BTC'; 

    // if you want to find out your open orders, you can use the below code,
    if ($exchange->has['fetchOpenOrders']) {
        $open_orders = $exchange->fetchOpenOrders($symbol);
    } else if ($exchange->has['fetchOrders']) {
        $all_orders = $exchange->fetchOrders($symbol);
        $open_orders = $exchange->filter_by($all_orders, 'status', 'open');
    } else {
        echo ($exchange->id . ' fetch(Open)Orders not supported yet');
    }

    // now, depending the $open_orders array, fill the below ID
    $orderId = 'xxxxxxxx'; 

    // to cancel multiple orders together asynchronously, see the "async-await-multiple.php" example file to adopt the code
    $exchange->cancel_order($orderId, $symbol);

} catch (\ccxt\NetworkError $e) {
    echo '[Network Error] ' . $e->getMessage() . "\n";
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}

```

## High-Level Overview

This is a PHP file located at `examples/php/cancel-order.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 24
- Comment lines: 4
- Blank lines: 8

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
php examples/php/cancel-order.php
```

