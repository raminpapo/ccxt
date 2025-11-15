# Documentation: examples/ccxt.pro/js/binance-fetch-balance-snapshot-watch-balance-updates.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/binance-fetch-balance-snapshot-watch-balance-updates.js`
- **Size**: 1,676 bytes
- **Lines**: 56
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt')

console.log ('CCXT Version:', ccxt.version)

// This example will run silent and will return your balance only when the balance is updated.
//
// 1. launch the example with your keys and keep it running
// 2. go to the trading section on the website
// 3. place a order on a spot market
// 4. see your balance updated in the example
//
// Warning! This example might produce a lot of output to your screen


async function watchBalance (exchange) {
    let balance = await exchange.fetchBalance ()
    console.log ('---------------------------------------------------------')
    console.log (exchange.iso8601 (exchange.milliseconds ()))
    console.log (balance, '\n')
    while (true) {
        try {
            const update = await exchange.watchBalance ()
            balance = exchange.deep_extend (balance, update)
            // it will print the balance update when the balance changes
            // if the balance remains unchanged the exchange will not send it
            console.log ('---------------------------------------------------------')
            console.log (exchange.iso8601 (exchange.milliseconds ()))
            console.log (balance, '\n')
        } catch (e) {
            console.log (e.constructor.name, e.message)
            break
        }
    }
}


async function main() {

     const exchange = new ccxt.pro.binance ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })

    await exchange.loadMarkets ()

    // exchange.verbose = true // uncomment for debugging purposes if necessary

    await watchBalance (exchange)

    await exchange.close ()
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/binance-fetch-balance-snapshot-watch-balance-updates.js`.

**Functions defined**: main, watchBalance



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 31
- Comment lines: 11
- Blank lines: 14

### Main Components

**Functions** (2):
- `main()`
- `watchBalance()`



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
node examples/ccxt.pro/js/binance-fetch-balance-snapshot-watch-balance-updates.js
```

