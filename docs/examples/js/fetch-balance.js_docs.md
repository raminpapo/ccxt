# Documentation: examples/js/fetch-balance.js

## File Metadata

- **Path**: `examples/js/fetch-balance.js`
- **Size**: 723 bytes
- **Lines**: 28
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
"use strict";

const ccxt      = require ('../../ccxt.js');

// instantiate the exchange
let exchange = new ccxt.coinbasepro  ({
    'apiKey': 'XXXXXXXXXXXXXX',
    'secret': 'YYYYYYYYYYYYYY',
    'password': 'ZZZZZZ', // if exchange requires password
});


async function checkMyBalance() {
    try {
        // fetch account balance from the exchange
        let myBalance = await exchange.fetchBalance ();

        // output the result
        console.log (exchange.id, 'fetched balance', myBalance);

    } catch (e) {
        // fpr advanced error-handling, see the "advanced-error-handling.js" example file
        console.log ('[' + e.constructor.name + '] ' + e.message);
        throw e;
    }
}

checkMyBalance();
```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-balance.js`.

**Functions defined**: checkMyBalance



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 17
- Comment lines: 4
- Blank lines: 7

### Main Components

**Functions** (1):
- `checkMyBalance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/fetch-balance.js
```

