# Documentation: examples/php/bytetrade-create-order.php

## File Metadata

- **Path**: `examples/php/bytetrade-create-order.php`
- **Size**: 637 bytes
- **Lines**: 29
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

echo 'PHP v' . PHP_MAJOR_VERSION . '.' . PHP_MINOR_VERSION . '.' . PHP_RELEASE_VERSION . "\n";
echo 'CCXT v' . \ccxt\Exchange::VERSION . "\n";

$exchange = new \ccxt\bytetrade(array(
    // replace with your keys
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET',
));

$exchange->load_markets();
$exchange->verbose = true;

$symbol = 'BTC/USDT';
$type = 'limit';
$side = 'buy';
$amount = 0.000865;
$price = 11560;

$order = $exchange->create_order($symbol, $type, $side, $amount, $price);
print_r ($order);

```

## High-Level Overview

This is a PHP file located at `examples/php/bytetrade-create-order.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 19
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
php examples/php/bytetrade-create-order.php
```

