# Documentation: examples/php/bitfinex2-fetch-trades-since.php

## File Metadata

- **Path**: `examples/php/bitfinex2-fetch-trades-since.php`
- **Size**: 467 bytes
- **Lines**: 23
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$id = 'bitfinex2';

// instantiate the exchange by id
$exchange = '\\ccxt\\' . $id;
$exchange = new $exchange ();

// load all markets from the exchange
$trades = $exchange->fetch_trades ('ETH/BTC', 1518983548636 - 2 * 24 * 60 * 60 * 1000);

foreach ($trades as $trade) {
    echo $trade['datetime'] . "\n";
}
echo count ($trades) . " trades\n";

?>
```

## High-Level Overview

This is a PHP file located at `examples/php/bitfinex2-fetch-trades-since.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 13
- Comment lines: 2
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
php examples/php/bitfinex2-fetch-trades-since.php
```

