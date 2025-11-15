# Documentation: examples/js/how-to-import-one-exchange-esm.js

## File Metadata

- **Path**: `examples/js/how-to-import-one-exchange-esm.js`
- **Size**: 287 bytes
- **Lines**: 11
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { binance } from '../../js/ccxt.js';
async function example() {
    const exchange = new binance({});
    const ob = await exchange.fetchOrderBook('BTC/USDT', 3);
    const asks = ob['asks'];
    const bids = ob['bids'];
    console.log(asks);
    console.log(bids);
}
example();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/how-to-import-one-exchange-esm.js`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 11
- Code lines: 10
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `example()`



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
node examples/js/how-to-import-one-exchange-esm.js
```

