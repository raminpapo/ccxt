# Documentation: wiki/examples/js/hitbtc2-withdraw.md

## File Metadata

- **Path**: `wiki/examples/js/hitbtc2-withdraw.md`
- **Size**: 2,080 bytes
- **Lines**: 66
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Hitbtc2 Withdraw](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import ololog from 'ololog';
const log       = ololog.configure ({ locate: false })

require ('ansicolor').nice

const getPositiveAccounts = function (balance) {
    const result = {}
    Object.keys (balance)
        .filter (currency => balance[currency] && (balance[currency] > 0))
        .forEach (currency => {
            result[currency] = balance[currency]
        })
    return result
}

;(async () => {

    // instantiate the exchange
    let exchange = new ccxt.hitbtc2  ({
        "apiKey": "YOUR_API_KEY",
        "secret": "YOUR_SECRET",
    })

    try {

        let tradingBalance = await exchange.fetchBalance ()
        let accountBalance = await exchange.fetchBalance ({ type: 'account' })

        log.cyan    ('Trading balance:', getPositiveAccounts (tradingBalance.total))
        log.magenta ('Account balance:', getPositiveAccounts (accountBalance.total))

        // withdraw
        let withdraw = await exchange.withdraw ('ETH', 0.01, '0x811DCfeb6dC0b9ed825808B6B060Ca469b83fB81')

        // output the result
        log (exchange.name.green, 'withdraw', withdraw)

    } catch (e) {

        if (e instanceof ccxt.DDoSProtection || e.message.includes ('ECONNRESET')) {
            log.bright.yellow ('[DDoS Protection] ' + e.message)
        } else if (e instanceof ccxt.RequestTimeout) {
            log.bright.yellow ('[Request Timeout] ' + e.message)
        } else if (e instanceof ccxt.AuthenticationError) {
            log.bright.yellow ('[Authentication Error] ' + e.message)
        } else if (e instanceof ccxt.ExchangeNotAvailable) {
            log.bright.yellow ('[Exchange Not Available Error] ' + e.message)
        } else if (e instanceof ccxt.ExchangeError) {
            log.bright.yellow ('[Exchange Error] ' + e.message)
        } else if (e instanceof ccxt.NetworkError) {
            log.bright.yellow ('[Network Error] ' + e.message)
        } else {
            throw e
        }
    }

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/hitbtc2-withdraw.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 47
- Comment lines: 3
- Blank lines: 16

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `ololog` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

