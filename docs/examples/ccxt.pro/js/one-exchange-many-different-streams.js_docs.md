# Documentation: examples/ccxt.pro/js/one-exchange-many-different-streams.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/one-exchange-many-different-streams.js`
- **Size**: 1,020 bytes
- **Lines**: 46
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt')

console.log ('CCXT Version:', ccxt.version)

async function watchOrders(exchange) {
    while (true) {
        try {
            const orders = await exchange.watchOrders() // await here
            console.log(orders)
        } catch (e) {
            console.log(e)
        }
    }
}

async function watchBalance(exchange) {
    while (true) {
        try {
            const balance = await exchange.watchBalance() // await here
            console.log(balance)
        } catch (e) {
            console.log(e)
        }
    }
}

async function main() {
     const exchange = new ccxt.pro.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'password': 'IF NECESSARY',
        // etc...
    })
    await exchange.loadMarkets () // await here

    // exchange.verbose = true // uncomment for debugging purposes if necessary

    watchOrders(exchange) // no await
    watchBalance(exchange) // no await

    await exchange.close()
}

main()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/one-exchange-many-different-streams.js`.

**Functions defined**: main, watchOrders, watchBalance



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 35
- Comment lines: 2
- Blank lines: 9

### Main Components

**Functions** (3):
- `main()`
- `watchBalance()`
- `watchOrders()`



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
node examples/ccxt.pro/js/one-exchange-many-different-streams.js
```

