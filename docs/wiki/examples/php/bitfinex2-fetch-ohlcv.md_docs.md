# Documentation: wiki/examples/php/bitfinex2-fetch-ohlcv.md

## File Metadata

- **Path**: `wiki/examples/php/bitfinex2-fetch-ohlcv.md`
- **Size**: 424 bytes
- **Lines**: 24
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitfinex2 Fetch Ohlcv](./examples/php/)


 ```php
 <?php

include './ccxt.php';

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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/bitfinex2-fetch-ohlcv.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 15
- Comment lines: 1
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

