# Documentation: wiki/examples/js/okex-transfer.md

## File Metadata

- **Path**: `wiki/examples/js/okex-transfer.md`
- **Size**: 1,674 bytes
- **Lines**: 56
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Okex Transfer](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/okex-transfer.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 32
- Comment lines: 10
- Blank lines: 14

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

