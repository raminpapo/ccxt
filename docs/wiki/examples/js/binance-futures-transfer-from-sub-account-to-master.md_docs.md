# Documentation: wiki/examples/js/binance-futures-transfer-from-sub-account-to-master.md

## File Metadata

- **Path**: `wiki/examples/js/binance-futures-transfer-from-sub-account-to-master.md`
- **Size**: 1,269 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Futures Transfer From Sub Account To Master](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

console.log ('CCXT Version:', ccxt.version)

// https://github.com/ccxt/ccxt/issues/10181

async function main () {

    const exchange = new ccxt.binance ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })

    const markets = await exchange.loadMarkets ()

    // exchange.verbose = true // uncomment for debugging purposes

    const fromEmail = 'sender@example.com' // edit for your values
        , toEmail = 'receiver@example.com' // edit for your values
        , code = 'USDT' // edit for your values
        , amount = 100 // edit for your values
        , futuresType = 1 // 1 for USDT-margined futures，2 for coin-margined futures

    const currency = exchange.currency (code);

    const response = await exchange.sapiPostSubAccountFuturesInternalTransfer ({
        'fromEmail': fromEmail, // sender email
        'toEmail': toEmail, // recipient email
        'futuresType': futuresType, // 1 for USDT-margined futures，2 for coin-margined futures
        'asset': currency['id'],
        'amount': exchange.currencyToPrecision (code, amount),
    })

    console.log (response)

}

main ()

 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/binance-futures-transfer-from-sub-account-to-master.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 27
- Comment lines: 2
- Blank lines: 18

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

