# Documentation: wiki/examples/js/huobi-futures.md

## File Metadata

- **Path**: `wiki/examples/js/huobi-futures.md`
- **Size**: 2,177 bytes
- **Lines**: 77
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Huobi Futures](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

const exchange = new ccxt.huobi ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'options': {
        'defaultType': 'future',
    },
})

;(async () => {
    const markets = await exchange.loadMarkets ()

    // exchange.verbose = true // uncomment for debugging purposes if necessary

    // creating and canceling a linear future (limit) order
    let symbol = 'ETH/USDT:USDT-220121' // the last segment is the date of expiration (can be next week, next quarter, ...) adjust it accordingly
    let type = 'limit'
    let side = 'buy'
    let offset= 'open'
    let leverage = 1
    let amount = 1
    let price = 1
    let params = {
        'offset': offset,
        'lever_rate': leverage,
    }

    try {
        // fetching current balance
        const balance = await exchange.fetchBalance()
        // console.log(balance)

        // placing an order
        const order = await exchange.createOrder (symbol, type, side, amount, price, params)
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

    // creating and canceling a inverse future (limit) order
    symbol = 'ADA/USD:ADA-220121' // the last segment is the date of expiration (can be next week, next quarter, ...) adjust it accordingly
    type = 'limit'
    side = 'buy'
    offset= 'open'
    leverage = 1
    amount = 1
    price = 1 // 1 contract = 10 ADA = 10 usd in this case
    params = {
        'offset': offset,
        'lever_rate': leverage,
    }

    try {
        const order = await exchange.createOrder (symbol, type, side, amount, price, params)
        console.log (order)
        const cancel = await exchange.cancelOrder (order['id'], symbol)
        console.log (cancel)
    } catch (e) {
        console.log (e.constructor.name, e.message)
    }

}) ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/huobi-futures.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 77
- Code lines: 55
- Comment lines: 8
- Blank lines: 14

### Main Components

**Constants** (1):
- `ADA`



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

