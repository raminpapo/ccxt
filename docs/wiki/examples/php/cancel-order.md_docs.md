# Documentation: wiki/examples/php/cancel-order.md

## File Metadata

- **Path**: `wiki/examples/php/cancel-order.md`
- **Size**: 1,196 bytes
- **Lines**: 41
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Cancel Order](./examples/php/)


 ```php
 <?php
include dirname(dirname(dirname(__FILE__))) . '/ccxt.php';
date_default_timezone_set('UTC');

$exchange = new \ccxt\binance(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET',
    // 'verbose' => true,
));

try {

    $symbol = 'XRP/BTC'; 

    // if you want to find out your open orders, you can use the below code,
    if ($exchange->has['fetchOpenOrders']) {
        $open_orders = $exchange->fetchOpenOrders($symbol);
    } else if ($exchange->has['fetchOrders']) {
        $all_orders = $exchange->fetchOrders($symbol);
        $open_orders = $exchange->filter_by($all_orders, 'status', 'open');
    } else {
        echo ($exchange->id . ' fetch(Open)Orders not supported yet');
    }

    // now, depending the $open_orders array, fill the below ID
    $orderId = 'xxxxxxxx'; 

    // to cancel multiple orders together asynchronously, see the "async-await-multiple.php" example file to adopt the code
    $exchange->cancel_order($orderId, $symbol);

} catch (\ccxt\NetworkError $e) {
    echo '[Network Error] ' . $e->getMessage() . "\n";
} catch (Exception $e) {
    echo '[Error] ' . $e->getMessage() . "\n";
}
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/php/cancel-order.md`.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 27
- Comment lines: 4
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this Markdown file:**

