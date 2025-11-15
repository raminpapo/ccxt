# Documentation: examples/js/load-all-symbols-at-once.js

## File Metadata

- **Path**: `examples/js/load-all-symbols-at-once.js`
- **Size**: 2,476 bytes
- **Lines**: 70
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import ololog from 'ololog';
import ansicolor from 'ansicolor';
const log       = ololog.configure ({ locate: false })

ansicolor.nice

//-----------------------------------------------------------------------------

process.on ('uncaughtException',  e => { log.bright.red.error (e); process.exit (1) })
process.on ('unhandledRejection', e => { log.bright.red.error (e); process.exit (1) })

//-----------------------------------------------------------------------------

let test = async function (exchange) {

    try {

        await exchange.loadMarkets ()
        log (exchange.id.green, 'loaded', exchange.symbols.length.toString ().bright.green, 'symbols')

    } catch (e) {

        if (e instanceof ccxt.DDoSProtection) {
            log.bright.yellow (exchange.id, '[DDoS Protection] ' + e.message)
        } else if (e instanceof ccxt.RequestTimeout) {
            log.bright.yellow (exchange.id, '[Request Timeout] ' + e.message)
        } else if (e instanceof ccxt.AuthenticationError) {
            log.bright.yellow (exchange.id, '[Authentication Error] ' + e.message)
        } else if (e instanceof ccxt.ExchangeNotAvailable) {
            log.bright.yellow (exchange.id, '[Exchange Not Available] ' + e.message)
        } else if (e instanceof ccxt.ExchangeError) {
            log.bright.yellow (exchange.id, '[Exchange Error] ' + e.message)
        } else if (e instanceof ccxt.NetworkError) {
            log.bright.yellow (exchange.id, '[Network Error] ' + e.message)
        } else {
            throw e
        }
    }
}

//-----------------------------------------------------------------------------

let exchanges = []

async function main () {

    // instantiate all exchanges
    await Promise.all (ccxt.exchanges.map (async id => {
        let exchange = new (ccxt)[id] ()
        exchanges.push (exchange)
        await test (exchange)
    }))

    let succeeded = exchanges.filter (exchange => exchange.markets ? true : false).length.toString ().bright.green
    let failed = exchanges.filter (exchange => exchange.markets ? false : true).length
    let total = ccxt.exchanges.length.toString ().bright.white
    let numSymbols = 0;
    exchanges.map (exchange => {
        numSymbols += exchange.symbols ? exchange.symbols.length : 0;
    })
    log (numSymbols, 'symbols from', succeeded, 'of', total, 'exchanges loaded', ('(' + failed + ' errors)').red)

}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/load-all-symbols-at-once.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 47
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
- `ololog` (imported)
- `ansicolor` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/load-all-symbols-at-once.js
```

