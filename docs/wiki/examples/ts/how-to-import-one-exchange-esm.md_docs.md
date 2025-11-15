# Documentation: wiki/examples/ts/how-to-import-one-exchange-esm.md

## File Metadata

- **Path**: `wiki/examples/ts/how-to-import-one-exchange-esm.md`
- **Size**: 368 bytes
- **Lines**: 17
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [How To Import One Exchange Esm](./examples/ts/)


 ```javascript
 import { binance } from '../../js/ccxt.js';

async function example () {
    const exchange = new binance ({});
    const ob = await exchange.fetchOrderBook ('BTC/USDT', 3);
    const asks = ob['asks'];
    const bids = ob['bids'];
    console.log (asks);
    console.log (bids);
}
example ();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/ts/how-to-import-one-exchange-esm.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 13
- Comment lines: 0
- Blank lines: 4

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

