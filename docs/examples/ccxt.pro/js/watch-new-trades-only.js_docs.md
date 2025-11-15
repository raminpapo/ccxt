# Documentation: examples/ccxt.pro/js/watch-new-trades-only.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/watch-new-trades-only.js`
- **Size**: 1,135 bytes
- **Lines**: 44
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt');

console.log ('CCXT Version:', ccxt.version);

async function watchExchange (exchangeId, symbol) {

     const exchange = new ccxt.pro[exchangeId] ({
        newUpdates: true,
    })

    await exchange.loadMarkets ();

    // exchange.verbose = true // uncomment for debugging purposes if necessary

    while (true) {
        try {
            const trades = await exchange.watchTrades (symbol)
            for (let i = 0; i < trades.length; i++) {
                const trade = trades[i]
                console.log (exchange.iso8601 (exchange.milliseconds ()), exchange.id, trade['symbol'], trade['id'], trade['datetime'], trade['price'], trade['amount'])
            }
        } catch (e) {
            console.log (symbol, e)
        }
    }
}

async function main () {

    const streams = {
        'binance': 'BTC/USDT',
        'okex': 'BTC/USDT',
        'kraken': 'BTC/USD',
    };

    const values = Object.entries (streams)
    const promises = values.map (([ exchangeId, symbol ]) => watchExchange (exchangeId, symbol))
    await Promise.all (promises)
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/watch-new-trades-only.js`.

**Functions defined**: main, watchExchange



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 31
- Comment lines: 1
- Blank lines: 12

### Main Components

**Functions** (2):
- `main()`
- `watchExchange()`



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
node examples/ccxt.pro/js/watch-new-trades-only.js
```

