# Documentation: examples/ccxt.pro/js/watch-many-exchanges-many-ordersbooks.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/watch-many-exchanges-many-ordersbooks.js`
- **Size**: 977 bytes
- **Lines**: 38
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt');

async function watchOrderBook (exchange, symbol) {
    while (true) {
        try {
            const orderbook = await exchange.watchOrderBook (symbol)
            console.log (new Date (), exchange.id, symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (symbol, e)
        }
    }
}

async function watchExchange (exchangeId, symbols) {
     const exchange = new ccxt.pro[exchangeId] ()
    await exchange.loadMarkets ()
    await Promise.all (symbols.map (symbol => watchOrderBook (exchange, symbol)))
}

async function main () {
    const streams = {
        'binance': [
            'BTC/USDT',
            'ETH/BTC',
        ],
        'ftx': [
            'BTC/USDT',
            'ETH/BTC',
        ],
    };

    const entries = Object.entries (streams)
    await Promise.all (entries.map (([ exchangeId, symbols ]) => watchExchange (exchangeId, symbols)))
}

main()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/watch-many-exchanges-many-ordersbooks.js`.

**Functions defined**: watchOrderBook, main, watchExchange



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 32
- Comment lines: 0
- Blank lines: 6

### Main Components

**Functions** (3):
- `main()`
- `watchExchange()`
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
node examples/ccxt.pro/js/watch-many-exchanges-many-ordersbooks.js
```

