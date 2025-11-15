# Documentation: examples/ccxt.pro/js/binance-watch-ticker-many-symbols.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/binance-watch-ticker-many-symbols.js`
- **Size**: 1,838 bytes
- **Lines**: 63
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt');

// your version must be 0.7+
console.log ('CCXT Version:', ccxt.version)

function handle (exchange, symbol, ticker) {
    console.log (new Date (), exchange.id, symbol, ticker['last'])
}

async function loop (exchange, symbol) {
    while (true) {
        try {
            const ticker = await exchange.watchTicker (symbol)
            handle (exchange, symbol, ticker)
        } catch (e) {
            console.log (symbol, e)
            // do nothing and retry on next loop iteration
            // throw e // uncomment to break all loops in case of an error in any one of them
            // break // you can also break just this one loop if it fails
        }
    }
}

async function main () {

     const exchange = new ccxt.pro.binanceusdm () // usd(s)-margined contracts
    //
    // or
    //
    //  const exchange = new ccxt.pro.binance () // spot markets
    //
    // WARNING: when using the spot markets mind subscription limits!
    // don't attempt to subscribe to all of them
    // the exchanges will not allow that in general
    // instead, specify a shorter list of symbols to subscribe to
    //
    // or
    //
    //  const exchange = new ccxt.pro.binancecoinm () // coin-margined contracts

    if (exchange.has['watchTicker']) {
        await exchange.loadMarkets ()
        // many symbols
        await Promise.all (exchange.symbols.map (symbol => loop (exchange, symbol)))
        //
        // or
        //
        // const symbols = [ 'BTC/USDT', 'ETH/USDT' ] // specific symbols
        // await Promise.all (symbols.map (symbol => loop (exchange, symbol)))
        //
        // or
        //
        // await loop (exchange, 'BTC/USDT') // one symbol

    } else {
        console.log (exchange.id, 'does not support watchTicker yet')
    }
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/binance-watch-ticker-many-symbols.js`.

**Functions defined**: loop, handle, main



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 26
- Comment lines: 27
- Blank lines: 10

### Main Components

**Functions** (3):
- `handle()`
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
node examples/ccxt.pro/js/binance-watch-ticker-many-symbols.js
```

