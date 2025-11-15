# Documentation: examples/ccxt.pro/js/exchange-close.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/exchange-close.js`
- **Size**: 1,147 bytes
- **Lines**: 46
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt')

console.log ("CCXT Pro Version:", ccxt.version)

const orderbooks = {}

let run = true

async function watchOrderBook (exchange, symbol) {
    while (run) {
        try {
            const orderbook = await exchange.watchOrderBook (symbol)
            orderbooks[symbol] = orderbook
            console.log (exchange.iso8601 (exchange.milliseconds ()), orderbook['datetime'], orderbook['nonce'], symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (e.constructor.name, e.message)
        }
    }
}


async function stop (exchange) {
    await exchange.sleep (10000)
    run = false
    await exchange.close ()
}


async function main () {
     const exchange = new ccxt.pro.binance ()
    await exchange.loadMarkets ()
    exchange.verbose = true
    const symbols = [
        'BTC/USDT',
        'ETH/USDT',
    ]
    stop (exchange).then (() => {})
    await Promise.all (symbols.map (symbol => watchOrderBook (exchange, symbol)))
    console.log ('Sleeping for a moment...')
    await exchange.sleep (10000)
    console.log ('Done')
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/exchange-close.js`.

**Functions defined**: watchOrderBook, stop, main



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 36
- Comment lines: 0
- Blank lines: 10

### Main Components

**Functions** (3):
- `main()`
- `stop()`
- `watchOrderBook()`



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
node examples/ccxt.pro/js/exchange-close.js
```

