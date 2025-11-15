# Documentation: wiki/examples/js/watchOrderBookForSymbols.md

## File Metadata

- **Path**: `wiki/examples/js/watchOrderBookForSymbols.md`
- **Size**: 461 bytes
- **Lines**: 17
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Watchorderbookforsymbols](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
async function example() {
    const binance = new ccxt.pro.binance({});
    const symbol = ['BTC/USDT', 'ETH/USDT', 'DOGE/USDT'];
    while (true) {
        const orderbook = await binance.watchOrderBookForSymbols(symbol);
        console.log(orderbook['symbol'], orderbook['asks'][0], orderbook['bids'][0]);
    }
}
await example();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/watchOrderBookForSymbols.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 13
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

