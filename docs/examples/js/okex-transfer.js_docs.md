# Documentation: examples/js/okex-transfer.js

## File Metadata

- **Path**: `examples/js/okex-transfer.js`
- **Size**: 1,617 bytes
- **Lines**: 51
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

console.log ('CCXT version:', ccxt.version)
console.log ('This example requires CCXT version 1.54.92 or higher')

async function main () {

    const exchange = new ccxt.okex ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'password': 'YOUR_API_KEY_PASSWORD',
    })

    await exchange.loadMarkets ()

    const code = 'USDT'
    let tradingBalance = await exchange.fetchFreeBalance (/* { 'type': 'trading' } */)
    let fundingBalance = await exchange.fetchFreeBalance ({ 'type': 'funding' })
    console.log ('Trading:', tradingBalance[code], code)
    console.log ('Funding:', fundingBalance[code], code)

    const oldVerboseMode = exchange.verbose
    exchange.verbose = process.argv.includes ('--verbose') || process.argv.includes ('-v')

    // https://www.okex.com/docs-v5/en/#rest-api-funding-funds-transfer
    //
    //     'spot' == '1'
    //     'futures' == '3',
    //     'margin' == '5',
    //     'swap' == '9',
    //     'option' == '12',
    //     'trading' == '18', // unified trading account
    //     'unified' == '18',
    //
    const from = 'trading'
    const to = 'funding'
    const amount = 1
    const transfer = await exchange.transfer (code, amount, from, to)
    console.log (transfer)

    exchange.verbose = oldVerboseMode

    tradingBalance = await exchange.fetchFreeBalance (/* { 'type': 'spot' } */)
    fundingBalance = await exchange.fetchFreeBalance ({ 'type': 'funding' })
    console.log ('Trading:', tradingBalance[code], code)
    console.log ('Funding:', fundingBalance[code], code)
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/okex-transfer.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 51
- Code lines: 29
- Comment lines: 10
- Blank lines: 12

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
node examples/js/okex-transfer.js
```

