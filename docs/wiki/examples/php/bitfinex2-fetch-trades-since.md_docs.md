# Documentation: wiki/examples/php/bitfinex2-fetch-trades-since.md

## File Metadata

- **Path**: `wiki/examples/php/bitfinex2-fetch-trades-since.md`
- **Size**: 480 bytes
- **Lines**: 26
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitfinex2 Fetch Trades Since](./examples/php/)


 ```php
 <?php

include './ccxt.php';

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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/bitfinex2-fetch-trades-since.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 15
- Comment lines: 2
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

