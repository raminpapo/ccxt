# Documentation: examples/ccxt.pro/js/gateio-watch-order-book.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/gateio-watch-order-book.js`
- **Size**: 2,316 bytes
- **Lines**: 71
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt')

console.log ("CCXT Pro Version:", ccxt.version)

const orderbooks = {}

async function watchAllSymbols (exchange, symbols) {
    while (true) {
        const keys = Object.keys (orderbooks);
        if (symbols.length === keys.length) {
            console.log ('\n\n\n\n\n')
            console.log ('----------------------------------------------------')
            console.log ('All orderbooks received at least one update:');
            for (let i = 0; i < symbols.length; i++) {
                const symbol = symbols[i]
                const orderbook = orderbooks[symbol]
                console.log (exchange.iso8601 (exchange.milliseconds ()), orderbook['datetime'], orderbook['nonce'], symbol, orderbook['asks'][0], orderbook['bids'][0])
            }
            console.log ('----------------------------------------------------')
            console.log ('\n\n\n\n\n')
            // process.exit () // stop here if you want
            break
        } else {
            await exchange.sleep (1000);
        }
    }
}

async function watchOrderBook (exchange, symbol) {
    while (true) {
        try {
            const orderbook = await exchange.watchOrderBook (symbol)
            orderbooks[symbol] = orderbook
            console.log (exchange.iso8601 (exchange.milliseconds ()), orderbook['datetime'], orderbook['nonce'], symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (e.constructor.name, e.message)
        }
    }
}

async function main () {
     const exchange = new ccxt.pro.gateio ({
        'options': {
            'defaultType': 'swap',
        },
    })
    await exchange.loadMarkets ()
    // exchange.verbose = true // uncomment for debugging purposes if necessary
    const symbols = [
        // 'SOS/USDT:USDT',
        // 'JASMY/USDT:USDT',
        // 'SLP/USDT:USDT',
        'ACH/USDT:USDT',
        'MKISHU/USDT:USDT',
        // 'GMT/USDT:USDT',
        // 'ASTR/USDT:USDT',
        'RAMP/USDT:USDT',
        'RSR/USDT:USDT',
        // 'RACA/USDT:USDT',
        // 'ROOK/USDT:USDT',
        // 'ROSE/USDT:USDT',
    ]
    await Promise.all ([
        watchAllSymbols (exchange, symbols),
        ... symbols.map (symbol => watchOrderBook (exchange, symbol))
    ])
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/gateio-watch-order-book.js`.

**Functions defined**: watchOrderBook, watchAllSymbols, main



## Detailed Walkthrough

### Code Structure

- Total lines: 71
- Code lines: 54
- Comment lines: 10
- Blank lines: 7

### Main Components

**Functions** (3):
- `main()`
- `watchAllSymbols()`
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
node examples/ccxt.pro/js/gateio-watch-order-book.js
```

