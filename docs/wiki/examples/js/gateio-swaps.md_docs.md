# Documentation: wiki/examples/js/gateio-swaps.md

## File Metadata

- **Path**: `wiki/examples/js/gateio-swaps.md`
- **Size**: 2,118 bytes
- **Lines**: 80
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Gateio Swaps](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

const exchange = new ccxt.gateio ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
    'options': {
        'defaultType': 'swap',
    },
})

;(async () => {
    // exchange.setSandboxMode (true)

    const markets = await exchange.loadMarkets ()

    exchange.verbose = true // uncomment for debugging purposes if necessary

    // Example 1: Creating and canceling a linear swap (limit) order
    try {
        const symbol = 'LTC/USDT:USDT'
        const type = 'limit'
        const side = 'buy'
        const amount = 1
        const price = 55

        // placing an order
        const order = await exchange.createOrder (symbol, type, side, amount, price)
        console.log (order)

        // fetching open orders
        const openOrders = await exchange.fetchOpenOrders(symbol)
        console.log(openOrders)

        // canceling an order
        const cancel = await exchange.cancelOrder (order['id'], symbol)
        console.log (cancel)
    } catch (e) {
        console.log (e.constructor.name, e.message)
    }

    // Example 2: Creating and canceling a linear swap (stop-limit) order with leverage
    try {
        const symbol = 'LTC/USDT:USDT'
        const type = 'limit'
        const side = 'buy'
        const amount = 1
        const price = 55

        const stopPrice = 130
        const params = {
            'stopPrice': stopPrice,
        }
        //set leverage
        const leverage = await exchange.setLeverage(3, symbol);
        console.log(leverage)

        // placing an order
        const order = await exchange.createOrder (symbol, type, side, amount, price, params)
        console.log (order)

        // canceling an order
        const cancelParams = {
            isStop: true,
        };
        const cancel = await exchange.cancelOrder (order['id'], symbol, cancelParams)
        console.log (cancel)

        //reset leverage
        exchange.setLeverage(1, symbol);
    } catch (e) {
        console.log (e.constructor.name, e.message)
    }

}) ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/gateio-swaps.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 53
- Comment lines: 10
- Blank lines: 17

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

