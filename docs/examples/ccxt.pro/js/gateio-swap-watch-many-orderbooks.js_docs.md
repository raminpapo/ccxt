# Documentation: examples/ccxt.pro/js/gateio-swap-watch-many-orderbooks.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/gateio-swap-watch-many-orderbooks.js`
- **Size**: 887 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt')

console.log ("CCXT Pro Version:", ccxt.version)

async function loop (exchange, method, symbol) {
    while (true) {
        try {
            const orderbook = await exchange[method] (symbol)
            console.log (exchange.iso8601 (exchange.milliseconds ()), orderbook['datetime'], orderbook['nonce'], symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (e.constructor.name, e.message)
        }
    }
}

async function main () {
     const exchange = new ccxt.pro.gateio ({
        'options': {'defaultType':'swap'}
    })
    await exchange.loadMarkets ()
    // exchange.verbose = true // uncomment for debugging purposes if necessary
    const symbols = [
        'ANC/USDT:USDT',
    ]
    await Promise.all (symbols.map (symbol => loop (exchange, 'fetchOrderBook', symbol)))
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/gateio-swap-watch-many-orderbooks.js`.

**Functions defined**: loop, main



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 24
- Comment lines: 1
- Blank lines: 5

### Main Components

**Functions** (2):
- `loop()`
- `main()`



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
node examples/ccxt.pro/js/gateio-swap-watch-many-orderbooks.js
```

