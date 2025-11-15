# Documentation: wiki/examples/php/huobi-swaps.md

## File Metadata

- **Path**: `wiki/examples/php/huobi-swaps.md`
- **Size**: 1,054 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Huobi Swaps](./examples/php/)


 ```php
 <?php

include './ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\huobipro(array(
    'apiKey' => 'YOUR_API_KEY', // ←------------ replace with your keys
    'secret' => 'YOUR_SECRET_KEY',
    // 'verbose' => true, // uncomment if debug output is needed
));

try {

    $markets = $exchange->load_markets ();

    // creating a linear swap (limit) order
    $symbol = 'ADA/USDT:USDT';
    $order_type = 'limit';
    $side = 'buy';
    $offset = 'open';
    $leverage = 1;
    $amount = 1;
    $price = 1;

    $params = array (
        'offset' => $offset,
        'lever_rate' => $leverage,
    );

    $order = $exchange->create_order ($symbol, $order_type, $side, $amount, $price, $params);
    var_dump ($order['id']);

} catch (\ccxt\NetworkError $e) {
    echo '[Network Error] ' . $e->getMessage() . "\n";
} catch (\ccxt\ExchangeError $e) {
    echo '[Exchange Error] ' . $e->getMessage() . "\n";
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}

?>
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/huobi-swaps.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 33
- Comment lines: 2
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

