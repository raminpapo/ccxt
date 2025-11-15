# Documentation: examples/ccxt.pro/js/watch-trades-many-symbols.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/watch-trades-many-symbols.js`
- **Size**: 726 bytes
- **Lines**: 29
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt');

console.log ('CCXT Version:', ccxt.version)

async function watchTrades (exchange, symbol) {

    while (true) {
        try {
            const trades = await exchange.watchTrades (symbol)
            console.log (new Date (), exchange.id, symbol, trades.length, 'trades')
        } catch (e) {
            console.log (symbol, e)
        }
    }
}

async function main () {
    const symbols = [ 'USDT/THB', 'BTC/THB', 'ETH/THB' ]
     const exchange = new ccxt.pro.zipmex({
        'newUpdates': true
    })
    const markets = await exchange.loadMarkets ()
    exchange.verbose = true
    await Promise.all (symbols.map ((symbol) => watchTrades (exchange, symbol)))
}

main()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/watch-trades-many-symbols.js`.

**Functions defined**: watchTrades, main



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 23
- Comment lines: 0
- Blank lines: 6

### Main Components

**Functions** (2):
- `main()`
- `watchTrades()`



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
node examples/ccxt.pro/js/watch-trades-many-symbols.js
```

