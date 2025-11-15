# Documentation: wiki/examples/js/basic-orderbook-polling.md

## File Metadata

- **Path**: `wiki/examples/js/basic-orderbook-polling.md`
- **Size**: 460 bytes
- **Lines**: 18
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Basic Orderbook Polling](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/basic-orderbook-polling.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 11
- Comment lines: 0
- Blank lines: 7

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

**To execute this Markdown file:**

