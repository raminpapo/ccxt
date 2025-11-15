# Documentation: examples/js/fetch-tickers/src/index.js

## File Metadata

- **Path**: `examples/js/fetch-tickers/src/index.js`
- **Size**: 674 bytes
- **Lines**: 18
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// Example code in typescript
// Based on /examples/js/fetch-from-many-exchanges-simultaneously.js
import * as ccxt from 'ccxt';
const log = require('ololog');
const symbol = 'BTC/USD';
const exchanges = ['coinbasepro', 'gemini', 'kraken'];
const fetchTickers = async (symbol) => {
    const result = await Promise.all(exchanges.map(async (id) => {
        const CCXT = ccxt; // Hack!
        const exchange = new CCXT[id]({ 'enableRateLimit': true });
        const ticker = await exchange.fetchTicker(symbol);
        const exchangeExtended = exchange.extend({ 'exchange': id }, ticker);
        return exchangeExtended;
    }));
    log(result);
};
fetchTickers(symbol);

```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-tickers/src/index.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 2
- Blank lines: 1

### Main Components

**Constants** (1):
- `CCXT`



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
node examples/js/fetch-tickers/src/index.js
```

