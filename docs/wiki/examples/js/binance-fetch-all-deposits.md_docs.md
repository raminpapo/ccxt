# Documentation: wiki/examples/js/binance-fetch-all-deposits.md

## File Metadata

- **Path**: `wiki/examples/js/binance-fetch-all-deposits.md`
- **Size**: 1,402 bytes
- **Lines**: 50
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Fetch All Deposits](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/binance-fetch-all-deposits.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 34
- Comment lines: 1
- Blank lines: 15

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

**To execute this Markdown file:**

