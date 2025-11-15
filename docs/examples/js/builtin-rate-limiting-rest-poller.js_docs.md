# Documentation: examples/js/builtin-rate-limiting-rest-poller.js

## File Metadata

- **Path**: `examples/js/builtin-rate-limiting-rest-poller.js`
- **Size**: 580 bytes
- **Lines**: 25
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import log from 'ololog';
import { nice as ansi } from 'ansicolor';
import asTable from 'as-table';

const exchange = new ccxt.coinbasepro ()
const repeat   = 100

async function test (symbol) {

    for (let i = 0; i < repeat; i++) {
        let ticker = await exchange.fetchTicker (symbol)
        log (exchange.id.green, exchange.iso8601 (exchange.milliseconds ()), ticker['datetime'], symbol.green, ticker['last'])
    }
}

const concurrent = [
    test ('BTC/USD'),
    test ('ETH/BTC'),
    test ('ETH/USD')
]

Promise.all (concurrent)
```

## High-Level Overview

This is a JavaScript file located at `examples/js/builtin-rate-limiting-rest-poller.js`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 18
- Comment lines: 0
- Blank lines: 7

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
- `as-table` (imported)
- `ololog` (imported)
- `ansicolor` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/builtin-rate-limiting-rest-poller.js
```

