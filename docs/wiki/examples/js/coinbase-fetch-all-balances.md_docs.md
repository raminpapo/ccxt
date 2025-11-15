# Documentation: wiki/examples/js/coinbase-fetch-all-balances.md

## File Metadata

- **Path**: `wiki/examples/js/coinbase-fetch-all-balances.md`
- **Size**: 1,444 bytes
- **Lines**: 44
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Fetch All Balances](./examples/js/)


 ```javascript
 "use strict";

const ccxt = require ('../../js/ccxt.js')

console.log ('CCXT Version:', ccxt.version)

async function fetchAllBalances (exchange) {
    const params = {}
    let balance = {}
    while (true) {
        const response = await exchange.fetchBalance (params)
        balance = exchange.extend (balance, response)
        const info = exchange.safeValue (response, 'info', {})
        const pagination = exchange.safeValue (info, 'pagination', {})
        const startingAfter = exchange.safeString (pagination, 'next_starting_after')
        if (startingAfter !== undefined) {
            params['starting_after'] = startingAfter
        } else {
            break
        }
    }
    return balance
}

async function main () {
    const exchange = new ccxt.coinbase ({
        // Value is the "name" field in the api_key.json file Coinbase will offer for download
        apiKey: 'organizations/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/apiKeys/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx',
        // This is the "privateKey" field in that JSON file
        secret: '-----BEGIN EC PRIVATE KEY-----\nxxx...xxx==\n-----END EC PRIVATE KEY-----',
    })
    const markets = await exchange.loadMarkets ()
    // coinbase.verbose = true // uncomment for debugging purposes if necessary
    const balance = await fetchAllBalances (exchange)
    console.log (balance)
}

main ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/coinbase-fetch-all-balances.md`.

**Functions defined**: fetchAllBalances, main



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 33
- Comment lines: 3
- Blank lines: 8

### Main Components

**Functions** (2):
- `fetchAllBalances()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

