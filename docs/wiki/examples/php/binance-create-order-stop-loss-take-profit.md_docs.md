# Documentation: wiki/examples/php/binance-create-order-stop-loss-take-profit.md

## File Metadata

- **Path**: `wiki/examples/php/binance-create-order-stop-loss-take-profit.md`
- **Size**: 1,560 bytes
- **Lines**: 55
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Create Order Stop Loss Take Profit](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

echo 'PHP v' . PHP_MAJOR_VERSION . '.' . PHP_MINOR_VERSION . '.' . PHP_RELEASE_VERSION . "\n";
echo 'CCXT v' . \ccxt\Exchange::VERSION . "\n";

$id = 'binanceusdm'; // edit this line

// ----------------------------------------------------------------------------

// instantiate the exchange by id
$exchange_class = '\\ccxt\\' . $id;
$exchange = new $exchange_class(array(
    // some exchanges may require additional API credentials
    'apiKey' => 'YOUR_API_KEY', // edit this line
    'secret' => 'YOUR_SECRET', // edit this line
));

$exchange->load_markets();
// $exchange->verbose = True; // uncomment for debugging purposes

$symbol = 'BTC/USDT';
$side = 'buy';
$amount = 0.01;
$stopLossPrice = 25000;
$takeProfitPrice = 35000;

try {

    $order = $exchange->create_order($symbol, 'MARKET', $side, $amount);
    print_r($order);

    $inverted_side = ($side == 'buy') ? 'sell' : 'buy';

    $stopLossParams = array('stopPrice' => $stopLossPrice);
    $stopLossOrder = $exchange->create_order($symbol, 'STOP_MARKET', $inverted_side, $amount, null, $stopLossParams);
    print_r($stopLossOrder);

    $takeProfitParams = array('stopPrice' => $takeProfitPrice);
    $takeProfitOrder = $exchange->create_order($symbol, 'TAKE_PROFIT_MARKET', $inverted_side , $amount, null, $takeProfitParams);
    print_r($takeProfitOrder);

} catch (Exception $e) {
    echo get_class($e) . ': ' . $e->getMessage() . "\n";
}

 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/binance-create-order-stop-loss-take-profit.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 33
- Comment lines: 4
- Blank lines: 18

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `apiKey` (imported)
- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

