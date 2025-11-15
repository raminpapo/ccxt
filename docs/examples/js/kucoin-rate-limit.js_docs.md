# Documentation: examples/js/kucoin-rate-limit.js

## File Metadata

- **Path**: `examples/js/kucoin-rate-limit.js`
- **Size**: 1,173 bytes
- **Lines**: 39
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

async function main () {

    const exchange = new ccxt.kucoin()
    const markets = await exchange.loadMarkets ()
    const timeframe = '5m'
    const symbol = 'BTC/USDT'
    const since = undefined
    const limit = 1000

    let i = 0
    while (true) {
        try {
            const ohlcvs = await exchange.fetchOHLCV(symbol, timeframe, since, limit)
            const now = exchange.milliseconds()
            const datetime = exchange.iso8601(now)
            console.log(datetime, i, 'fetched', ohlcvs.length, symbol, timeframe, 'candles',
                'from', exchange.iso8601(ohlcvs[0][0]),
                'to', exchange.iso8601(ohlcvs[ohlcvs.length-1][0]))
        } catch (e) {
            if (e instanceof ccxt.RateLimitExceeded) {
                const now = exchange.milliseconds()
                const datetime = exchange.iso8601(now)
                console.log(datetime, i, e.constructor.name, e.message)
                await exchange.sleep(10000)
            } else {
                console.log(e.constructor.name, e.message)
                throw e
            }
        }
        i += 1
    }
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/kucoin-rate-limit.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 32
- Comment lines: 0
- Blank lines: 7

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/kucoin-rate-limit.js
```

