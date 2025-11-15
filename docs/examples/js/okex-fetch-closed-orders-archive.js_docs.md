# Documentation: examples/js/okex-fetch-closed-orders-archive.js

## File Metadata

- **Path**: `examples/js/okex-fetch-closed-orders-archive.js`
- **Size**: 622 bytes
- **Lines**: 31
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

console.log ('CCXT Version:', ccxt.version)

// https://github.com/ccxt/ccxt/issues/10179

async function main () {

    const exchange = new ccxt.okex ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'password': 'YOUR_PASSWORD',
        'options': {
            'fetchClosedOrders': {
                'method': 'privateGetTradeOrdersHistoryArchive'
            }
        }
    })

    const markets = await exchange.loadMarkets ()

    exchange.verbose = true

    const orders = await exchange.fetchClosedOrders ()
    console.log (orders)

}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/okex-fetch-closed-orders-archive.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 19
- Comment lines: 1
- Blank lines: 11

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

**To execute this JavaScript file:**

```bash
node examples/js/okex-fetch-closed-orders-archive.js
```

