# Documentation: examples/js/basic-orderbook-polling.js

## File Metadata

- **Path**: `examples/js/basic-orderbook-polling.js`
- **Size**: 393 bytes
- **Lines**: 13
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';

const id = 'huobipro', exchange = new ccxt[id] ({ enableRateLimit: true }), symbol = 'ETH/BTC';(async function main () {

    await exchange.loadMarkets ()

    for (let i = 0; i < 2000; i++) {

        const orderbook = await exchange.fetchOrderBook (symbol)
        console.log (new Date (), i, symbol, orderbook.asks[0], orderbook.bids[0])
    }

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/basic-orderbook-polling.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 8
- Comment lines: 0
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

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/basic-orderbook-polling.js
```

