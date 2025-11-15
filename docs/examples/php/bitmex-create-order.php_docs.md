# Documentation: examples/php/bitmex-create-order.php

## File Metadata

- **Path**: `examples/php/bitmex-create-order.php`
- **Size**: 621 bytes
- **Lines**: 28
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\bitmex(array(
    'apiKey' => 'YOUR_API_KEY', // ←------------ replace with your keys
    'secret' => 'YOUR_SECRET',
));

$symbol = 'BTC/USD:BTC-220624';
$type = 'StopLimit'; // # or 'market', or 'Stop' or 'StopLimit'
$side = 'sell'; // or 'buy'
$amount = 1.0;
$price = 6500.0; // or None

// extra params and overrides
$params = array(
    'stopPx' => 6000.0, // if needed
);

$order = $exchange->create_order($symbol, $type, $side, $amount, $price, $params);

print_r($order);

```

## High-Level Overview

This is a PHP file located at `examples/php/bitmex-create-order.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 18
- Comment lines: 1
- Blank lines: 9

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
php examples/php/bitmex-create-order.php
```

