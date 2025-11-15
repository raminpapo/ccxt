# Documentation: examples/js/binance-fetch-all-deposits.js

## File Metadata

- **Path**: `examples/js/binance-fetch-all-deposits.js`
- **Size**: 1,332 bytes
- **Lines**: 45
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

(async function main () {

    const exchange = new ccxt.binance ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })

    await exchange.loadMarkets ()

    // exchange.verbose = true // uncomment for debugging

    const ninetyDays = 90 * 24 * 60 * 60 * 1000;
    let startTime = exchange.parse8601 ('2018-01-01T00:00:00')
    const now = exchange.milliseconds ()
    const currencyCode = undefined // any currency

    let allTransactions = []

    while (startTime < now) {

        const endTime = startTime + ninetyDays

        const transactions = await exchange.fetchDeposits (currencyCode, startTime, undefined, {
            'endTime': endTime,
        })
        if (transactions.length) {
            const lastTransaction = transactions[transactions.length - 1]
            startTime = lastTransaction['timestamp'] + 1
            allTransactions = allTransactions.concat (transactions)
        } else {
            startTime = endTime;
        }
    }

    console.log ('Fetched', allTransactions.length, 'transactions')
    for (let i = 0; i < allTransactions.length; i++) {
        const transaction = allTransactions[i]
        console.log (i, transaction['datetime'], transaction['txid'], transaction['currency'], transaction['amount'])
    }

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/binance-fetch-all-deposits.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 31
- Comment lines: 1
- Blank lines: 13

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
node examples/js/binance-fetch-all-deposits.js
```

