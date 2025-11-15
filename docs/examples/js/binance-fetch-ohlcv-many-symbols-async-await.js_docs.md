# Documentation: examples/js/binance-fetch-ohlcv-many-symbols-async-await.js

## File Metadata

- **Path**: `examples/js/binance-fetch-ohlcv-many-symbols-async-await.js`
- **Size**: 1,256 bytes
- **Lines**: 34
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../js/ccxt.js')

console.log('CCXT Version:', ccxt.version)

async function symbolLoop (exchange, symbol, timeframe) {
    while (true) {
        try {
            const ohlcvs = await exchange.fetchOHLCV (symbol, timeframe)
            console.log (exchange.iso8601 (exchange.milliseconds ()), exchange.id, symbol, ohlcvs.length, 'OHLCV candles received')
            // await exchange.sleep (60 * 1000) // sleep if necessary, though not required
        } catch (e) {
            console.log (exchange.iso8601 (exchange.milliseconds ()), exchange.id, symbol, e.constructor.name, e.message)
        }
    }
}

async function main () {
    const exchange = new ccxt.binance ()
    await exchange.loadMarkets ()
    // exchange.verbose = true // uncomment for debugging purposes if necessary
    const symbols = [
        'BTC/USDT', // unified symbols used here as opposed to exchange-specific market ids
        'ETH/USDT', // more about unified symbols vs exchange-specific ids here:
        'ADA/USDT', // https://github.com/ccxt/ccxt/wiki/Manual#markets
    ]
    const timeframe = '1m'
    const loops = symbols.map (symbol => symbolLoop (exchange, symbol, timeframe))
    await Promise.all (loops)
}


main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/binance-fetch-ohlcv-many-symbols-async-await.js`.

**Functions defined**: symbolLoop, main



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 26
- Comment lines: 2
- Blank lines: 6

### Main Components

**Functions** (2):
- `main()`
- `symbolLoop()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/binance-fetch-ohlcv-many-symbols-async-await.js
```

