# Documentation: wiki/examples/ts/watchPositionsForSymbols.md

## File Metadata

- **Path**: `wiki/examples/ts/watchPositionsForSymbols.md`
- **Size**: 498 bytes
- **Lines**: 22
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Watchpositionsforsymbols](./examples/ts/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const exchange = new ccxt.pro.binanceusdm ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'Your_API_SECRET'
    });
    const symbols = [ 'BTC/USDT:USDT', 'ETH/USDT:USDT', 'DOGE/USDT:USDT' ];
    while (true) {
        const trades = await exchange.watchPositions (symbols);
        console.log (trades);
    }
}
await example ();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/ts/watchPositionsForSymbols.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 16
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

