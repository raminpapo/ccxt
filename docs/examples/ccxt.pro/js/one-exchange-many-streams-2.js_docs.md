# Documentation: examples/ccxt.pro/js/one-exchange-many-streams-2.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/one-exchange-many-streams-2.js`
- **Size**: 843 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt');

(async () => {

     const exchange = new ccxt.pro.binance ({ enableRateLimit: true })
    const symbols = [ 'BTC/USDT', 'ETH/BTC', 'ETH/USDT' ]

    const loop = async (symbol) => {
        while (true) {
            try {
                const orderbook = await exchange.watchOrderBook (symbol)
                console.log (new Date (), symbol, orderbook['asks'][0], orderbook['bids'][0])
            } catch (e) {
                console.log (symbol, e)
                // do nothing and retry on next loop iteration
                // throw e // uncomment to break all loops in case of an error in any one of them
                // break // you can also break just this one loop if it fails
            }
        }
    }

    await Promise.all (symbols.map (symbol => loop (symbol)))

}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/one-exchange-many-streams-2.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 17
- Comment lines: 3
- Blank lines: 7

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
node examples/ccxt.pro/js/one-exchange-many-streams-2.js
```

