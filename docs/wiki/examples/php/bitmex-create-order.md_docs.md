# Documentation: wiki/examples/php/bitmex-create-order.md

## File Metadata

- **Path**: `wiki/examples/php/bitmex-create-order.md`
- **Size**: 625 bytes
- **Lines**: 31
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitmex Create Order](./examples/php/)


 ```php
 <?php

include './ccxt.php';

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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/bitmex-create-order.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 20
- Comment lines: 1
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

