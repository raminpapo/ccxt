# Documentation: examples/ccxt.pro/js/watch-many-orderbooks.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/watch-many-orderbooks.js`
- **Size**: 674 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt');

async function watchOrderBook (exchangeId, symbol) {

     const exchange = new ccxt.pro[exchangeId] ()
    while (true) {
        try {
            const orderbook = await exchange.watchOrderBook (symbol)
            console.log (new Date (), exchange.id, symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (symbol, e)
        }
    }
}

async function main () {
    const streams = {
        'binance': 'BTC/USDT',
        'ftx': 'BTC/USDT',
    };

    await Promise.all (Object.entries (streams).map (([ exchangeId, symbol ]) => watchOrderBook (exchangeId, symbol)))
}

main()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/watch-many-orderbooks.js`.

**Functions defined**: watchOrderBook, main



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 21
- Comment lines: 0
- Blank lines: 6

### Main Components

**Functions** (2):
- `main()`
- `watchOrderBook()`



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
node examples/ccxt.pro/js/watch-many-orderbooks.js
```

