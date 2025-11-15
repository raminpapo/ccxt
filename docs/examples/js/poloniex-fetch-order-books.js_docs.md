# Documentation: examples/js/poloniex-fetch-order-books.js

## File Metadata

- **Path**: `examples/js/poloniex-fetch-order-books.js`
- **Size**: 896 bytes
- **Lines**: 36
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


// ----------------------------------------------------------------------------

import ccxt from '../../js/ccxt.js';

// ----------------------------------------------------------------------------

(async () => {

    const exchange = new ccxt.poloniex ({
        'verbose': process.argv.includes ('--verbose'),
        'timeout': 60000,
    })

    try {

        const response = await exchange.fetchOrderBooks ([
            'ETH/BTC',
            'LTC/BTC',
            'OMG/BTC',
        ])
        console.log (response);
        console.log ('Succeeded.')

    } catch (e) {

        console.log ('--------------------------------------------------------')
        console.log (e.constructor.name, e.message)
        console.log ('--------------------------------------------------------')
        console.log (exchange.last_http_response)
        console.log ('Failed.')
    }

}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/poloniex-fetch-order-books.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 22
- Comment lines: 2
- Blank lines: 12

### Main Components



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
node examples/js/poloniex-fetch-order-books.js
```

