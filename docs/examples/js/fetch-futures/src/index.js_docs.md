# Documentation: examples/js/fetch-futures/src/index.js

## File Metadata

- **Path**: `examples/js/fetch-futures/src/index.js`
- **Size**: 902 bytes
- **Lines**: 26
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// Example code in typescript
// Based on /examples/js/fetch-okex-futures.js
import * as ccxt from 'ccxt';
const log = require('ololog');
const fetchFutures = async () => {
    const exchange = new ccxt.bitmex();
    exchange.markets = await exchange.loadMarkets(true);
    for (let symbol in exchange.markets) {
        log('----------------------------------------------------');
        log(`symbol = ${symbol}`);
        try {
            const market = exchange.markets[symbol];
            if (market['future']) {
                const ticker = await exchange.fetchTicker(symbol);
                log('----------------------------------------------------');
                log(symbol, ticker);
                await ccxt.sleep(exchange.rateLimit); // Missing type information.
            }
        }
        catch (error) {
            log('error =', error);
        }
    }
};
fetchFutures();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-futures/src/index.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 23
- Comment lines: 2
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `ccxt` (imported)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/fetch-futures/src/index.js
```

