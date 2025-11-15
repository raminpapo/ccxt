# Documentation: examples/ccxt.pro/js/watch-new-trades.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/watch-new-trades.js`
- **Size**: 1,285 bytes
- **Lines**: 43
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt');

(async () => {

    const streams = {
        'binance': 'BTC/USDT',
        'okex': 'BTC/USDT'
    };

    await Promise.all (Object.keys (streams).map (exchangeId =>

        (async () => {

             const exchange = new ccxt.pro[exchangeId] ({
                enableRateLimit: true,
                options: {
                    tradesLimit: 100, // lower = better, 1000 by default
                },
            })
            const symbol = streams[exchangeId]
            let lastId = ''
            while (true) {
                console.log ('---')
                try {
                    const trades = await exchange.watchTrades (symbol)
                    for (let i = 0; i < trades.length; i++) {
                        const trade = trades[i]
                        if (trade['id'] > lastId) {
                            console.log (exchange.iso8601 (exchange.milliseconds ()), exchange.id, trade['symbol'], trade['id'], trade['datetime'], trade['price'], trade['amount'])
                            lastId = trade['id']
                        }
                    }
                } catch (e) {
                    console.log (symbol, e)
                }
            }

        }) ())
    )
}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/watch-new-trades.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 35
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
node examples/ccxt.pro/js/watch-new-trades.js
```

