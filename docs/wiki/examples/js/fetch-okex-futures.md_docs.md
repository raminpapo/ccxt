# Documentation: wiki/examples/js/fetch-okex-futures.md

## File Metadata

- **Path**: `wiki/examples/js/fetch-okex-futures.md`
- **Size**: 554 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Okex Futures](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

async function test () {

    const exchange = new ccxt.okex ()
    await exchange.loadMarkets ()

    for (let symbol in exchange.markets) {

        const market = exchange.markets[symbol]

        if (market['future']) {
            console.log ('----------------------------------------------------')
            console.log (symbol, await exchange.fetchTicker (symbol))
            await ccxt.sleep (exchange.rateLimit)
        }
    }
}

test ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/fetch-okex-futures.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 17
- Comment lines: 0
- Blank lines: 11

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
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

