# Documentation: examples/ccxt.pro/js/apex-watch.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/apex-watch.js`
- **Size**: 2,233 bytes
- **Lines**: 75
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

import ccxt from '../../../js/ccxt.js';

// your version must be 0.7+
console.log ('CCXT Version:', ccxt.version)

function handle (exchange, symbol, ticker) {
    console.log (new Date (), exchange.id, symbol, ticker)
}

async function loop (exchange, symbol) {
    while (true) {
        try {
            const ticker = await exchange.watchMyTrades ()
            handle (exchange, symbol, ticker)
            sleep( 10000 )
        } catch (e) {
            console.log (symbol, e)
            // do nothing and retry on next loop iteration
            // throw e // uncomment to break all loops in case of an error in any one of them
            // break // you can also break just this one loop if it fails
        }
    }
}

async function main () {

     const exchange = new ccxt.pro.apex ({
         'apiKey': 'your api Key',
         'secret': 'your api secret',
         'walletAddress': 'your eth address',
         'options': {
             'accountId': 'your account id',
             'passphrase': 'your api passphrase',
             'seeds': 'your zklink omni seed',
             'brokerId': '',
         },
     }) // usd(s)-margined contracts
    exchange.setSandboxMode(true)
    //
    // or
    //
    //  const exchange = new ccxt.pro.binance () // spot markets
    //
    // WARNING: when using the spot markets mind subscription limits!
    // don't attempt to subscribe to all of them
    // the exchanges will not allow that in general
    // instead, specify a shorter list of symbols to subscribe to
    //
    // or
    //
    //  const exchange = new ccxt.pro.binancecoinm () // coin-margined contracts

    if (exchange.has['watchTicker']) {
        await exchange.loadMarkets ()
        // many symbols
        //await Promise.all (exchange.symbols.map (symbol => loop (exchange, symbol)))
        //
        // or
        //
        // const symbols = [ 'BTC/USDT', 'ETH/USDT' ] // specific symbols
        // await Promise.all (symbols.map (symbol => loop (exchange, symbol)))
        //
        // or
        //
        await loop (exchange, ['BTC-USDT','ETH-USDT']) // one symbol

    } else {
        console.log (exchange.id, 'does not support watchTicker yet')
    }
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/apex-watch.js`.

**Functions defined**: loop, handle, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 38
- Comment lines: 27
- Blank lines: 10

### Main Components

**Functions** (3):
- `handle()`
- `loop()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../js/ccxt.js` (imported)
- `../../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/ccxt.pro/js/apex-watch.js
```

