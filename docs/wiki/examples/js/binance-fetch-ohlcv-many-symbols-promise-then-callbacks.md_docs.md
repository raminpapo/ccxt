# Documentation: wiki/examples/js/binance-fetch-ohlcv-many-symbols-promise-then-callbacks.md

## File Metadata

- **Path**: `wiki/examples/js/binance-fetch-ohlcv-many-symbols-promise-then-callbacks.md`
- **Size**: 1,363 bytes
- **Lines**: 38
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Fetch Ohlcv Many Symbols Promise Then Callbacks](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/binance-fetch-ohlcv-many-symbols-promise-then-callbacks.md`.

**Functions defined**: symbolLoop, main



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 30
- Comment lines: 1
- Blank lines: 7

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

**To execute this Markdown file:**

