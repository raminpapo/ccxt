# Documentation: examples/js/create-order-ws-example.js

## File Metadata

- **Path**: `examples/js/create-order-ws-example.js`
- **Size**: 741 bytes
- **Lines**: 26
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
async function example() {
    const exchange = new ccxt.pro.binance({
        'apiKey': 'MY_API_KEY',
        'secret': 'MY_SECRET',
    });
    exchange.setSandboxMode(true);
    exchange.verbose = true; // uncomment for debugging purposes if necessary
    // load markets
    await exchange.loadMarkets();
    const symbol = 'ETH/USDT';
    const type = 'limit';
    const side = 'buy';
    const amount = 0.01;
    let price = 1000;
    let orders = [];
    for (let i = 1; i < 5; i++) {
        const response = await exchange.createOrderWs(symbol, type, side, amount, price);
        price += i;
        orders.push(response);
    }
    console.log(orders);
}
await example();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/create-order-ws-example.js`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 23
- Comment lines: 2
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
node examples/js/create-order-ws-example.js
```

