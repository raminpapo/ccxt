# Documentation: wiki/examples/js/fetch-ohlcv.md

## File Metadata

- **Path**: `wiki/examples/js/fetch-ohlcv.md`
- **Size**: 644 bytes
- **Lines**: 22
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Ohlcv](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
async function example() {
    const myex = new ccxt.okx({});
    const fromTimestamp = myex.milliseconds() - 86400 * 1000; // last 24 hrs
    const ohlcv = await myex.fetchOHLCV('BTC/USDT', '1m', fromTimestamp, 3, { 'whatever': 123 });
    const length = ohlcv.length;
    if (length > 0) {
        const lastPrice = ohlcv[length - 1][4];
        console.log('Fetched ', length, ' candles for ', myex.id, ':  last close ', lastPrice);
    }
    else {
        console.log('No candles have been fetched');
    }
}
await example();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/fetch-ohlcv.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 18
- Comment lines: 1
- Blank lines: 3

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

