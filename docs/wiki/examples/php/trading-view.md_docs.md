# Documentation: wiki/examples/php/trading-view.md

## File Metadata

- **Path**: `wiki/examples/php/trading-view.md`
- **Size**: 723 bytes
- **Lines**: 33
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Trading View](./examples/php/)


 ```php
 <?php

include './ccxt.php';

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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/trading-view.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 15
- Comment lines: 6
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

