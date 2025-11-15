# Documentation: examples/js/coinex-fetch-all-deposit-addresses-using-fetchDepositAddress.js

## File Metadata

- **Path**: `examples/js/coinex-fetch-all-deposit-addresses-using-fetchDepositAddress.js`
- **Size**: 1,193 bytes
- **Lines**: 48
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
"use strict";

const ccxt = require ('../../ccxt')

console.log ('CCXT Version:', ccxt.version)

// https://github.com/ccxt/ccxt/issues/15405

async function main () {
    
    const exchange = new ccxt.coinex ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET',
    });

    // exchange.verbose = true // uncomment for debugging purposes

    await exchange.loadMarkets ();
    const addresses = {};
    const promises = [];

    async function fetchDepositAddress (currency, network) {
        try {
            const response = await exchange.fetchDepositAddress(currency, { 'network': network });
            addresses[currency][network] = response['address']
        }
        catch (err) {
            console.error(err)
        }
    }    

    const currencies = Object.keys (exchange.currencies);

    for (const currency of currencies) {
        const networks = Object.keys (exchange.currencies[currency]['networks']);
        for (const network of networks) {
            addresses[currency] = {};
            promises.push (fetchDepositAddress (currency, network));
        }
    }

    await Promise.all (promises);

    console.log (addresses)
};

main ();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/coinex-fetch-all-deposit-addresses-using-fetchDepositAddress.js`.

**Functions defined**: main, fetchDepositAddress



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 32
- Comment lines: 2
- Blank lines: 14

### Main Components

**Functions** (2):
- `fetchDepositAddress()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/coinex-fetch-all-deposit-addresses-using-fetchDepositAddress.js
```

