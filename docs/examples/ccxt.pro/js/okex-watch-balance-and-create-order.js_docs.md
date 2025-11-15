# Documentation: examples/ccxt.pro/js/okex-watch-balance-and-create-order.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/okex-watch-balance-and-create-order.js`
- **Size**: 1,413 bytes
- **Lines**: 54
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
const ccxt = require ('ccxt')

console.log ('Node.js:', process.version)
console.log ('CCXT Pro v' + ccxt.version)

 const exchange = new ccxt.pro.okex ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    'password': 'YOUR_API_PASWORD'
})

async function watchBalance (code) {

    while (true) {
        const balance = await exchange.watchBalance ({
            'code': code,
        })
        console.log ('New', code, 'balance is: ', balance[code])
    }
}

async function createOrder (symbol, type, side, amount, price = undefined, params = {}) {

    console.log ('Creating', symbol, type, 'order')
    const order = await exchange.createOrder (symbol, type, side, amount, price, params);
    console.log (symbol, type, side, 'order created')
    console.log (order)
}

;(async () => {

    await exchange.loadMarkets ()
    console.log (exchange.id, 'markets loaded')

    const symbol = 'ETH/USDT'
    const market = exchange.market (symbol)
    const quote = market['quote']

    // run in parallel without await
    console.log ('Watching', quote, 'balance')
    watchBalance (quote)

    // wait a bit to allow it to subscribe
    await exchange.sleep (3000)

    const ticker = await exchange.watchTicker (symbol)
    const type = 'market'
    const side = 'buy'
    const amount = 0.1
    const price = ticker['bid']

    await createOrder (symbol, type, side, amount, price)

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/okex-watch-balance-and-create-order.js`.

**Functions defined**: watchBalance, createOrder



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 38
- Comment lines: 2
- Blank lines: 14

### Main Components

**Functions** (2):
- `createOrder()`
- `watchBalance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/ccxt.pro/js/okex-watch-balance-and-create-order.js
```

