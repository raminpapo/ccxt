# Documentation: wiki/examples/php/gateio-futures.md

## File Metadata

- **Path**: `wiki/examples/php/gateio-futures.md`
- **Size**: 1,245 bytes
- **Lines**: 54
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Gateio Futures](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\gateio(array(
    'apiKey' => 'YOUR_API_KEY', // ←------------ replace with your keys
    'secret' => 'YOUR_SECRET_KEY',
    'options' => array(
        'defaultType' => 'future',
    ),
    // 'verbose' => true, // uncomment if debug output is needed
));

// Example 1: Creating future (market) order
try {
    $markets = $exchange->load_markets ();

    // find a future
    $symbol = null;
    foreach($markets as $key => $market) {
        if ($market['future']) {
            $symbol = $market['symbol']; // example BTC/USDT:USDT-22031
            break;
        }
    }
    if ($symbol != null) {
        $type = 'market';
        $side = 'buy';
        $amount = 1;

        // placing an order
        $order = $exchange->create_order ($symbol, $type, $side, $amount);
        var_dump ($order);

        // listing open orders
        $open_orders = $exchange->fetch_open_orders($symbol);
        var_dump($open_orders);
    }

} catch (\ccxt\NetworkError $e) {
    echo '[Network Error] ' . $e->getMessage() . "\n";
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}

?>
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/gateio-futures.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 37
- Comment lines: 5
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

