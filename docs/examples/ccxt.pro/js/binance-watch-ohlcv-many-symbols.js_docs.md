# Documentation: examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols.js`
- **Size**: 2,059 bytes
- **Lines**: 65
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt');

// your version must be 0.7+
console.log ('CCXT Version:', ccxt.version)

function handle (exchange, symbol, timeframe, candles) {
    const lastCandle = candles[candles.length - 1]
    const lastClosingPrice = lastCandle[4]
    console.log (new Date (), exchange.id, timeframe, symbol, '\t', lastClosingPrice)
}

async function loop (exchange, symbol, timeframe) {
    while (true) {
        try {
            const candles = await exchange.watchOHLCV (symbol, timeframe)
            handle (exchange, symbol, timeframe, candles)
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

    if (exchange.has['watchOHLCV']) {
        await exchange.loadMarkets ()
        const timeframe = '15m'
        // many symbols
        await Promise.all (exchange.symbols.map (symbol => loop (exchange, symbol, timeframe)))
        //
        // or
        //
        // const symbols = [ 'BTC/USDT', 'ETH/USDT' ] // specific symbols
        // await Promise.all (symbols.map (symbol => loop (exchange, symbol, timeframe)))
        //
        // or
        //
        // await loop (exchange, 'BTC/USDT', timeframe) // one symbol
    } else {
        console.log (exchange.id, 'does not support watchOHLCV yet')
    }
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols.js`.

**Functions defined**: loop, handle, main



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 29
- Comment lines: 27
- Blank lines: 9

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
node examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols.js
```

