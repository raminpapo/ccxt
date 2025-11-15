# Documentation: wiki/examples/js/gateio-futures.md

## File Metadata

- **Path**: `wiki/examples/js/gateio-futures.md`
- **Size**: 1,347 bytes
- **Lines**: 55
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Gateio Futures](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';


const exchange = new ccxt.gateio ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
    'options': {
        'defaultType': 'future',
    },
})

;(async () => {
    // exchange.setSandboxMode (true)

    const markets = await exchange.loadMarkets ()

    // exchange.verbose = true // uncomment for debugging purposes if necessary

    // Example 1: Creating a future (market) order
    try {

        // find a future
        const futures = []
        for (const [key, market] of Object.entries(markets)) {
            if (market['future']) {
                futures.push(market);
            }
        }
        if (futures.length > 0) {
            const market = futures[0];
            const symbol = market['symbol'] // example: BTC/USDT:USDT-220318
            const type = 'market'
            const side = 'buy'
            const amount = 1

            // placing an order
            const order = await exchange.createOrder (symbol, type, side, amount)
            console.log (order)

            // fetching open orders
            const openOrders = await exchange.fetchOpenOrders(symbol)
            console.log(openOrders)
        }

    } catch (e) {
        console.log (e.constructor.name, e.message)
    }

}) ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/gateio-futures.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 35
- Comment lines: 6
- Blank lines: 14

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

