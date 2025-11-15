# Documentation: wiki/examples/js/order-book-extra-level-depth-param.md

## File Metadata

- **Path**: `wiki/examples/js/order-book-extra-level-depth-param.md`
- **Size**: 593 bytes
- **Lines**: 25
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Order Book Extra Level Depth Param](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import log from 'ololog';
import ansicolor from 'ansicolor';

ansicolor.nice

;(async function test () {

    const exchange = new ccxt.bitfinex ()
    const limit = 5
    const orders = await exchange.fetchOrderBook ('BTC/USD', limit, {
        // this parameter is exchange-specific, all extra params have unique names per exchange
        'group': 1, // 1 = orders are grouped by price, 0 = orders are separate
    })

    log (orders)
}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/order-book-extra-level-depth-param.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 16
- Comment lines: 1
- Blank lines: 8

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `ololog` (imported)
- `ansicolor` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

