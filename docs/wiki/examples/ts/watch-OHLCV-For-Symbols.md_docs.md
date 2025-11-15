# Documentation: wiki/examples/ts/watch-OHLCV-For-Symbols.md

## File Metadata

- **Path**: `wiki/examples/ts/watch-OHLCV-For-Symbols.md`
- **Size**: 475 bytes
- **Lines**: 23
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Watch Ohlcv For Symbols](./examples/ts/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const binance = new ccxt.pro.binance ({});
    const subscriptions = [
        [ 'BTC/USDT', '5m' ],
        [ 'ETH/USDT', '5m' ],
        [ 'BTC/USDT', '1h' ],
    ];
    while (true) {
        const ohlcv = await binance.watchOHLCVForSymbols (subscriptions);
        console.log (ohlcv);
    }
}
await example ();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/ts/watch-OHLCV-For-Symbols.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 17
- Comment lines: 1
- Blank lines: 5

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

**To execute this Markdown file:**

