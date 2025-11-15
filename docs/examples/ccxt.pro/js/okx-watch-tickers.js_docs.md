# Documentation: examples/ccxt.pro/js/okx-watch-tickers.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/okx-watch-tickers.js`
- **Size**: 972 bytes
- **Lines**: 32
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../../js/ccxt.js';

async function main() {
    const exchange = new ccxt.pro.okx()
    await exchange.loadMarkets()
    // exchange.verbose = true
    while (true) {
        try {

            // don't do this, specify a list of symbols to watch for watchTickers
            // or a very large subscription message will crash your WS connection
            // const tickers = await exchange.watchTickers ()

            // do this instead
            const symbols = [
                'ETH/BTC',
                'BTC/USDT',
                'ETH/USDT',
                // ...
            ]
            const tickers = await exchange.watchTickers (symbols)
            symbols = Object.keys(tickers)
            console.log (new Date(), 'received', symbols.length, 'symbols', ... symbols.slice(0,5).join(', '), '...')
        } catch (e) {
            console.log (new Date(), e.constructor.name, e.message)
            break
        }
    }
}

main()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/okx-watch-tickers.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 21
- Comment lines: 6
- Blank lines: 5

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../js/ccxt.js` (imported)
- `../../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/ccxt.pro/js/okx-watch-tickers.js
```

