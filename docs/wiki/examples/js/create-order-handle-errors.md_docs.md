# Documentation: wiki/examples/js/create-order-handle-errors.md

## File Metadata

- **Path**: `wiki/examples/js/create-order-handle-errors.md`
- **Size**: 1,369 bytes
- **Lines**: 61
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Create Order Handle Errors](./examples/js/)


 ```javascript
 

// ----------------------------------------------------------------------------

import ccxt from '../../js/ccxt.js';

// ----------------------------------------------------------------------------

(async () => {

    const exchange = new ccxt.bittrex ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET_KEY',
        'verbose': false, // set to true to see more debugging output
        'timeout': 60000,
    })

    // try to load markets first, retry on request timeouts until it succeeds:

    while (true) {

        try {

            await exchange.loadMarkets ();
            break;

        } catch (e) {

            if (e instanceof ccxt.RequestTimeout)
                console.log (exchange.iso8601 (Date.now ()), e.constructor.name, e.message)
        }
    }

    const symbol = 'ETH/BTC'
    const orderType = 'limit'
    const side = 'sell'
    const amount = 0.321;
    const price = 0.123;

    // try just one attempt to create an order

    try {

        const response = await exchange.createOrder (symbol, orderType, side, amount, price);
        console.log (response);
        console.log ('Succeeded');

    } catch (e) {

        console.log (exchange.iso8601 (Date.now ()), e.constructor.name, e.message)
        console.log ('Failed');

    }

}) ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/create-order-handle-errors.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 34
- Comment lines: 4
- Blank lines: 23

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

**To execute this Markdown file:**

