# Documentation: examples/js/create-trailing-percent-order.js

## File Metadata

- **Path**: `examples/js/create-trailing-percent-order.js`
- **Size**: 1,316 bytes
- **Lines**: 37
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
async function example() {
    const exchange = new ccxt.bingx({
        'apiKey': 'MY_API_KEY',
        'secret': 'MY_SECRET',
    });
    // exchange.setSandboxMode (true);
    // exchange.verbose = true; // uncomment for debugging purposes if necessary
    await exchange.loadMarkets();
    const symbol = 'BTC/USDT:USDT';
    const order_type = 'market';
    const side = 'sell';
    const amount = 0.0001;
    const price = undefined;
    const reduceOnly = true;
    const trailingPercent = 10;
    // const trailingTriggerPrice = undefined; // not supported on all exchanges
    const params = {
        'reduceOnly': reduceOnly,
        'trailingPercent': trailingPercent,
        // 'trailingTriggerPrice': trailingTriggerPrice,
    };
    try {
        const create_order = await exchange.createOrder(symbol, order_type, side, amount, price, params);
        // Alternatively use the createTrailingAmountOrder method:
        // const create_order = await exchange.createTrailingPercentOrder (symbol, order_type, side, amount, price, trailingPercent, trailingTriggerPrice, {
        //     'reduceOnly': reduceOnly,
        // });
        console.log(create_order);
    }
    catch (e) {
        console.log(e.toString());
    }
}
await example();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/create-trailing-percent-order.js`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 27
- Comment lines: 9
- Blank lines: 1

### Main Components

**Functions** (1):
- `example()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/create-trailing-percent-order.js
```

