# Documentation: examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols-continuously.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols-continuously.js`
- **Size**: 1,176 bytes
- **Lines**: 38
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
"use strict";

const ccxt = require ('ccxt')

const ohlcvsBySymbol = {}

function handleAllOHLCVs (exchange, ohlcvs, symbol, timeframe) {
    const now = exchange.iso8601 (exchange.milliseconds ())
    const lastCandle = exchange.safeValue (ohlcvs, ohlcvs.length - 1)
    const datetime = exchange.iso8601 (lastCandle[0])
    console.log (now, datetime, symbol, timeframe, lastCandle.slice (1))
}

async function pollOHLCV (exchange, symbol, timeframe) {
    await exchange.throttle (1000) // 1000ms delay between subscriptions
    while (true) {
        try {
            const response = await exchange.watchOHLCV (symbol, timeframe)
            ohlcvsBySymbol[symbol] = response
            handleAllOHLCVs(exchange, response, symbol, timeframe)
        } catch (e) {
            console.log (e.constructor.name, e.message)
        }
    }
}

async function main () {

     const exchange = new ccxt.pro.binance()
    const markets = await exchange.loadMarkets ()
    const timeframe = '5m'

    const firstOneHundredSymbols = exchange.symbols.slice (0, 100)

    await Promise.all (firstOneHundredSymbols.map (symbol => pollOHLCV (exchange, symbol, timeframe)))
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols-continuously.js`.

**Functions defined**: pollOHLCV, main, handleAllOHLCVs



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 29
- Comment lines: 0
- Blank lines: 9

### Main Components

**Functions** (3):
- `handleAllOHLCVs()`
- `main()`
- `pollOHLCV()`



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
node examples/ccxt.pro/js/binance-watch-ohlcv-many-symbols-continuously.js
```

