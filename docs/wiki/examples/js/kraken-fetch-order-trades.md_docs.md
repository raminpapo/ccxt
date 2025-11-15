# Documentation: wiki/examples/js/kraken-fetch-order-trades.md

## File Metadata

- **Path**: `wiki/examples/js/kraken-fetch-order-trades.md`
- **Size**: 964 bytes
- **Lines**: 39
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Kraken Fetch Order Trades](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

(async () => {

    const exchange = new ccxt.kraken ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        // 'verbose': true,
    })

    const orders = await exchange.fetchClosedOrders ();

    for (let i = 0; i < orders.length; i++) {
        const order = await exchange.fetchOrder (orders[i]['id']);
        const trades = await exchange.fetchOrderTrades (order['id'], undefined, undefined, undefined, order);
        console.log (trades);
    }

    //
    // alternatively:
    //
    // const params = {
    //     'trades': [
    //         'TT5UC3-GOIRW-6AZZ6R',
    //         'TIY6G4-LKLAI-Y3GD4A',
    //         'T57FVC-OB4LN-Z55WUL',
    //         'TIMIRG-WUNNE-RRJ6GT',
    //     ]
    // }
    //
    // const trades = await exchange.fetchOrderTrades (order['id'], undefined, undefined, undefined, params);

}) ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/kraken-fetch-order-trades.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 16
- Comment lines: 14
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

