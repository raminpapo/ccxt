# Documentation: examples/js/binance-fetch-ohlcv-many-symbols-promise-then-callbacks.js

## File Metadata

- **Path**: `examples/js/binance-fetch-ohlcv-many-symbols-promise-then-callbacks.js`
- **Size**: 1,264 bytes
- **Lines**: 33
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../js/ccxt.js')

console.log('CCXT Version:', ccxt.version)

function symbolLoop (exchange, symbol, timeframe) {
    exchange.fetchOHLCV (symbol, timeframe).then (ohlcvs => {
        console.log (exchange.iso8601 (exchange.milliseconds ()), exchange.id, symbol, ohlcvs.length, 'OHLCV candles received')
        setTimeout (() => symbolLoop (exchange, symbol, timeframe), 0)
    }).catch (e => {
        console.log (exchange.iso8601 (exchange.milliseconds ()), exchange.id, symbol, e.constructor.name, e.message)
        setTimeout (() => symbolLoop (exchange, symbol, timeframe), 0)
    })
}

function main () {
    const exchange = new ccxt.binance ()
    // exchange.verbose = true // uncomment for debugging purposes if necessary
    const symbols = [
        'BTC/USDT', // unified symbols used here as opposed to exchange-specific market ids
        'ETH/USDT', // more about unified symbols vs exchange-specific ids here:
        'ADA/USDT', // https://github.com/ccxt/ccxt/wiki/Manual#markets
    ]
    const timeframe = '1m'
    exchange.loadMarkets ().then (markets => {
        for (const symbol of symbols) {
            setTimeout (() => symbolLoop (exchange, symbol, timeframe), 0)
        }
    })
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/binance-fetch-ohlcv-many-symbols-promise-then-callbacks.js`.

**Functions defined**: symbolLoop, main



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 27
- Comment lines: 1
- Blank lines: 5

### Main Components

**Functions** (2):
- `main()`
- `symbolLoop()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/binance-fetch-ohlcv-many-symbols-promise-then-callbacks.js
```

