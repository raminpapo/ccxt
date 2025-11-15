# Documentation: examples/php/trading-view.php

## File Metadata

- **Path**: `examples/php/trading-view.php`
- **Size**: 726 bytes
- **Lines**: 30
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

// this example shows how to convert from CCXT OHLCV format to TradingView format
// and back from TradingView to OHLCV for various charting purposes/applications

$id = 'bittrex';
$symbol = 'ETH/BTC';

// instantiate the exchange by id
$exchange = '\\ccxt\\' . $id;
$exchange = new $exchange();

// OHLCV format by default
$ohlcv = $exchange->fetch_ohlcv($symbol);

// convert OHLCV → TradingView
$trading_view = $exchange->convert_ohlcv_to_trading_view($ohlcv);

// convert TradingView → OHCLV
$restored_ohlcvs = $exchange->convert_trading_view_to_ohlcv($trading_view);

print_r($restored_ohlcvs);

?>
```

## High-Level Overview

This is a PHP file located at `examples/php/trading-view.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 13
- Comment lines: 6
- Blank lines: 11

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
php examples/php/trading-view.php
```

