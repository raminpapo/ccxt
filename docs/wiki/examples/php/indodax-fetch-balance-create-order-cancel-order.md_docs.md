# Documentation: wiki/examples/php/indodax-fetch-balance-create-order-cancel-order.md

## File Metadata

- **Path**: `wiki/examples/php/indodax-fetch-balance-create-order-cancel-order.md`
- **Size**: 1,797 bytes
- **Lines**: 68
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Indodax Fetch Balance Create Order Cancel Order](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\indodax(array(
    'apiKey' => 'YOUR_API_KEY', // ←------------ replace with your keys
    'secret' => 'YOUR_SECRET',
));

//-----------------------------------------------------------------------------
// querying balance

$balance = $exchange->fetch_balance();

print_r($balance);

// do whatever you need here with your balance...

//-----------------------------------------------------------------------------
// placing and canceling orders

$symbol = 'BTC/IDR'; // bitcoin contract according to bitmex futures coding
$type = 'limit';
$side = 'sell'; // or 'buy'
$amount = 1.0;
$price = 6500.0; // or None

// extra params and overrides if necessary
$params = array(
    // ...
);

// buying

$buy_order1 = $exchange->create_limit_buy_order($symbol, $amount, $price, $params);
echo "Buy order 1:\n";
print_r($buy_order1);

$buy_order2 = $exchange->create_order($symbol, $type, 'buy', $amount, $price, $params);
//                             order side hardcoded here ↑ for example
echo "Buy order 2:\n";
print_r($buy_order2);

// selling

$sell_order1 = $exchange->create_limit_sell_order($symbol, $amount, $price, $params);
echo "Sell order 1:\n";
print_r($sell_order1);

$sell_order2 = $exchange->create_order ($symbol, $type, $side, $amount, $price, $params);
//                         order side from a variable here ↑ for example
echo "Sell order 2:\n";
print_r($sell_order2);

// canceling

$exchange->cancel_order($buy_order1['id'], $symbol);
$exchange->cancel_order($buy_order2['id'], $symbol);
$exchange->cancel_order($sell_order1['id'], $symbol);
$exchange->cancel_order($sell_order2['id'], $symbol);
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/indodax-fetch-balance-create-order-cancel-order.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 68
- Code lines: 35
- Comment lines: 12
- Blank lines: 21

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

