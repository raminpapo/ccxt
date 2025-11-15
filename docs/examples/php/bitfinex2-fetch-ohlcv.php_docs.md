# Documentation: examples/php/bitfinex2-fetch-ohlcv.php

## File Metadata

- **Path**: `examples/php/bitfinex2-fetch-ohlcv.php`
- **Size**: 418 bytes
- **Lines**: 21
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = '\\ccxt\\bitfinex2';
$exchange = new $exchange(array(
    'rateLimit' => 12000,
));

// bitfinex2 breaks occasionally

for ($i = 0; $i < 1000; $i++) {
    $ohlcv = $exchange->fetch_ohlcv('BTC/USD', '1m');
    print_r ($exchange->iso8601($ohlcv[0][0]) . "\t" . count($ohlcv) . "\n");
}

?>
```

## High-Level Overview

This is a PHP file located at `examples/php/bitfinex2-fetch-ohlcv.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 13
- Comment lines: 1
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
php examples/php/bitfinex2-fetch-ohlcv.php
```

