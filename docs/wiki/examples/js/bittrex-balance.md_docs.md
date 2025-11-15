# Documentation: wiki/examples/js/bittrex-balance.md

## File Metadata

- **Path**: `wiki/examples/js/bittrex-balance.md`
- **Size**: 1,589 bytes
- **Lines**: 55
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bittrex Balance](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import ansicolor from 'ansicolor';
import ololog from 'ololog'

const log = ololog.configure ({ locate: false })

ansicolor.nice

let sleep = (ms) => new Promise (resolve => setTimeout (resolve, ms))

;(async () => {

    // instantiate the exchange
    let exchange = new ccxt.bittrex  ({
        "apiKey": "471b47a06c384e81b24072e9a8739064",
        "secret": "694025686e9445589787e8ca212b4cff",
    })


    try {

        // fetch account balance from the exchange
        let balance = await exchange.fetchBalance ()

        // output the result
        log (exchange.name.green, 'balance', balance)

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
            throw e;
        }
    }

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/bittrex-balance.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 36
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
- `ansicolor` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

