# Documentation: examples/ccxt.pro/js/many-exchanges-many-streams.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/many-exchanges-many-streams.js`
- **Size**: 996 bytes
- **Lines**: 38
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt');

(async () => {

    const streams = {
        'binance': 'BTC/USDT',
        'bittrex': 'BTC/USDT',
        'poloniex': 'BTC/USDT',
        'bitfinex': 'BTC/USDT',
        'hitbtc': 'BTC/USDT',
        'upbit': 'BTC/USDT',
        'coinbasepro': 'BTC/USD',
        'ftx': 'BTC/USDT',
        'okex': 'BTC/USDT',
        'gateio': 'BTC/USDT',
    };

    await Promise.all (Object.keys (streams).map (exchangeId =>

        (async () => {

             const exchange = new ccxt.pro[exchangeId] ({ enableRateLimit: true })
            const symbol = streams[exchangeId]
            while (true) {
                try {
                    const orderbook = await exchange.watchOrderBook (symbol)
                    console.log (new Date (), exchange.id, symbol, orderbook['asks'][0], orderbook['bids'][0])
                } catch (e) {
                    console.log (symbol, e)
                }
            }

        }) ())
    )
}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/many-exchanges-many-streams.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 30
- Comment lines: 0
- Blank lines: 8

### Main Components



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
node examples/ccxt.pro/js/many-exchanges-many-streams.js
```

