# Documentation: wiki/examples/php/basic-order.md

## File Metadata

- **Path**: `wiki/examples/php/basic-order.md`
- **Size**: 791 bytes
- **Lines**: 42
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Basic Order](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\binance (array(
    'apiKey' => 'YOUR_API_KEY', // change for your keys
    'secret' => 'YOUR_API_SECRET',
));

$message = null;

try {

    $exchange->load_markets();

    $exchange->verbose = true; // uncomment for debugging purposes

    // adjust your values below

    $symbol = 'BTC/USDT';
    $order_type = 'limit';
    $side = 'sell';
    $amount = 0.123; // adjust for your amount
    $price = 50000; // adjust for your price (for limit orders)

    $result = $exchange->create_order ($symbol, $order_type, $side, $amount, $price);
    var_dump ($result);

} catch (Exception $e) {

    echo get_class($e) . ': ' . $e->getMessage() . "\n";
}

?>
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/basic-order.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 25
- Comment lines: 1
- Blank lines: 16

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

