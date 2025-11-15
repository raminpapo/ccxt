# Documentation: examples/js/fetch-orders.js

## File Metadata

- **Path**: `examples/js/fetch-orders.js`
- **Size**: 497 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import log from 'ololog';
import ansicolor from 'ansicolor';


ansicolor.nice

const exchange = new ccxt.bittrex ({
    apiKey: "YOUR_API_KEY",
    secret: "YOUR_SECRET",
})

async function test () {

    const orders = await exchange.fetchOrders ()

    log (asTable (orders.map (order => ccxt.omit (order, [ 'timestamp', 'info' ]))))

    const order = await exchange.fetchOrder (orders[0]['id'])

    log (order)
}

test ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-orders.js`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 16
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
- `ololog` (imported)
- `ansicolor` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/fetch-orders.js
```

