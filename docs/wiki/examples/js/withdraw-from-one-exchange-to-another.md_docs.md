# Documentation: wiki/examples/js/withdraw-from-one-exchange-to-another.md

## File Metadata

- **Path**: `wiki/examples/js/withdraw-from-one-exchange-to-another.md`
- **Size**: 1,520 bytes
- **Lines**: 56
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Withdraw From One Exchange To Another](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

console.log ('CCXT Version', ccxt.version)

async function main () {

    const binance = new ccxt.binance ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'options': {
            'fetchCurrencies': true,
        },
    })

    const kucoin = new ccxt.kucoin ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'password': 'YOUR_API_PASSWORD',
    })

    await binance.loadMarkets ()
    await kucoin.loadMarkets ()

    binance.verbose = true
    kucoin.verbose = true

    const code = 'COTI'
    const amount = 40

    // https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-api-params
    // https://binance-docs.github.io/apidocs/spot/en/#deposit-address-supporting-network-user_data
    const deposit = await binance.fetchDepositAddress (code, { 'network': 'ETH' })

    console.log ('-----------------------------------------------------------')

    console.log (depositAddress)

    console.log ('-----------------------------------------------------------')

    // https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-api-params
    // https://docs.kucoin.com/#apply-withdraw-2
    const withdrawal = await kucoin.withdraw (code, amount, deposit['address'], deposit['tag'], { 'chain': 'ERC20' })

    console.log ('-----------------------------------------------------------')

    console.log (withdrawal)

}

main ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/withdraw-from-one-exchange-to-another.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 33
- Comment lines: 4
- Blank lines: 19

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

