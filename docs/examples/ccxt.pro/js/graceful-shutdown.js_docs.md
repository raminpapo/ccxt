# Documentation: examples/ccxt.pro/js/graceful-shutdown.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/graceful-shutdown.js`
- **Size**: 973 bytes
- **Lines**: 43
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt');

let stop = false

async function shutdown (milliseconds) {
    await ccxt.sleep (10000)
    stop = true
}

async function watchOrderBook (exchangeId, symbol) {

     const exchange = new ccxt.pro[exchangeId] ()
    await exchange.loadMarkets ()
    // exchange.verbose = true
    while (!stop) {
        try {
            const orderbook = await exchange.watchOrderBook (symbol)
            console.log (new Date (), exchange.id, symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (symbol, e)
            stop = true
            break
        }
    }
    await exchange.close ()
}

async function main () {
    const streams = {
        'binance': 'BTC/USDT',
        'ftx': 'BTC/USDT',
    };

    await Promise.all ([
        shutdown (10000),
        ... Object.entries (streams).map (([ exchangeId, symbol ]) => watchOrderBook (exchangeId, symbol))
    ])

}

main()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/graceful-shutdown.js`.

**Functions defined**: shutdown, main, watchOrderBook



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 33
- Comment lines: 1
- Blank lines: 9

### Main Components

**Functions** (3):
- `main()`
- `shutdown()`
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
node examples/ccxt.pro/js/graceful-shutdown.js
```

