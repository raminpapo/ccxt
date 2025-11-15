# Documentation: examples/js/fetch-okex-futures.js

## File Metadata

- **Path**: `examples/js/fetch-okex-futures.js`
- **Size**: 492 bytes
- **Lines**: 23
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

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

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-okex-futures.js`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 14
- Comment lines: 0
- Blank lines: 9

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

**To execute this JavaScript file:**

```bash
node examples/js/fetch-okex-futures.js
```

