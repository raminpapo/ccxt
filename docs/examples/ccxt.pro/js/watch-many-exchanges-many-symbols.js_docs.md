# Documentation: examples/ccxt.pro/js/watch-many-exchanges-many-symbols.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/watch-many-exchanges-many-symbols.js`
- **Size**: 1,281 bytes
- **Lines**: 41
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt');

console.log ('CCXT Version:', ccxt.version)


async function watchTickerLoop (exchange, symbol) {
    // exchange.verbose = true // uncomment for debugging purposes if necessary
    while (true) {
        try {
            const ticker = await exchange.watchTicker (symbol)
            console.log (new Date (), exchange.id, symbol, ticker['last'])
        } catch (e) {
            console.log (symbol, e)
            // do nothing and retry on next loop iteration
            // throw e // uncomment to break all loops in case of an error in any one of them
            // break // you can also break just this one loop if it fails
        }
    }
}

async function exchangeLoop (exchangeId, symbols) {
     const exchange = new ccxt.pro[exchangeId]()
    await exchange.loadMarkets ()
    const loops = symbols.map (symbol => watchTickerLoop (exchange, symbol))
    await Promise.all (loops)
    await exchange.close ()
}

async function main () {
    const exchanges = {
        'binance': [ 'BTC/USDT', 'ETH/USDT' ],
        'ftx': [ 'BTC/USD', 'ETH/USD' ],
    }
    const loops = Object.entries (exchanges).map (([ exchangeId, symbols ]) => exchangeLoop (exchangeId, symbols))
    await Promise.all (loops)
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/watch-many-exchanges-many-symbols.js`.

**Functions defined**: exchangeLoop, main, watchTickerLoop



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 29
- Comment lines: 4
- Blank lines: 8

### Main Components

**Functions** (3):
- `exchangeLoop()`
- `main()`
- `watchTickerLoop()`



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
node examples/ccxt.pro/js/watch-many-exchanges-many-symbols.js
```

