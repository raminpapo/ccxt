# Documentation: wiki/examples/js/huobi-swaps.md

## File Metadata

- **Path**: `wiki/examples/js/huobi-swaps.md`
- **Size**: 1,993 bytes
- **Lines**: 76
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Huobi Swaps](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

const exchange = new ccxt.huobi ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
    'options': {
        'defaultType': 'swap',
    },
})

;(async () => {
    const markets = await exchange.loadMarkets ()

    // exchange.verbose = true // uncomment for debugging purposes if necessary

    // creating and canceling a linear swap (limit) order
    let symbol = 'ADA/USDT:USDT'
    let type = 'limit'
    let side = 'buy'
    let offset= 'open'
    let leverage = 1
    let amount = 1
    let price = 1 // 1 contract = 10 ADA = 10 usd in this case
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

    // creating and canceling an inverse swap (limit) order
    symbol = 'ADA/USD:ADA'
    type = 'limit'
    side = 'buy'
    offset = 'open'
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

This is a Markdown file located at `wiki/examples/js/huobi-swaps.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 55
- Comment lines: 8
- Blank lines: 13

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

