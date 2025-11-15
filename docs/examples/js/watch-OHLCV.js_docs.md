# Documentation: examples/js/watch-OHLCV.js

## File Metadata

- **Path**: `examples/js/watch-OHLCV.js`
- **Size**: 329 bytes
- **Lines**: 13
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
async function example() {
    const binance = new ccxt.pro.binance({});
    const symbol = 'BTC/USDT';
    const timeframe = '1m';
    while (true) {
        const ohlcv = await binance.watchOHLCV(symbol, timeframe);
        console.log(ohlcv);
    }
}
await example();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/watch-OHLCV.js`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 11
- Comment lines: 1
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
node examples/js/watch-OHLCV.js
```

