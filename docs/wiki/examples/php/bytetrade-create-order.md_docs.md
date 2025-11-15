# Documentation: wiki/examples/php/bytetrade-create-order.md

## File Metadata

- **Path**: `wiki/examples/php/bytetrade-create-order.md`
- **Size**: 644 bytes
- **Lines**: 32
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bytetrade Create Order](./examples/php/)


 ```php
 <?php

include './ccxt.php';

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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/bytetrade-create-order.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 21
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

