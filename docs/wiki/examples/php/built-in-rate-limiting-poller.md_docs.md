# Documentation: wiki/examples/php/built-in-rate-limiting-poller.md

## File Metadata

- **Path**: `wiki/examples/php/built-in-rate-limiting-poller.md`
- **Size**: 591 bytes
- **Lines**: 24
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Built In Rate Limiting Poller](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = '\\ccxt\\poloniex';
$exchange = new $exchange();

$symbol = 'DOGE/BTC';

while (true) {
    $order_book = $exchange->fetch_order_book($symbol);
    echo "----------------------------------------------------------------\n";
    echo date('c') . "\n";
    echo count($order_book['bids']) . " bids and " . count($order_book['asks']) . " asks\n";
    echo sprintf("bid: %.8f ask: %.8f", $order_book['bids'][0][0], $order_book['asks'][0][0]) . "\n";
}
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/built-in-rate-limiting-poller.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 16
- Comment lines: 0
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

