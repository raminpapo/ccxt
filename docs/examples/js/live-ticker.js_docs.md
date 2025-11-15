# Documentation: examples/js/live-ticker.js

## File Metadata

- **Path**: `examples/js/live-ticker.js`
- **Size**: 2,001 bytes
- **Lines**: 80
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import asTable from 'as-table';
import ololog from 'ololog';
import ansicolor from 'ansicolor';
import ccxt from '../../js/ccxt.js';

const { noLocate } = ololog;
const log = noLocate;

ansicolor.nice

let printSupportedExchanges = function () {
    log ('Supported exchanges:', ccxt.exchanges.join (', ').green)
}

let printUsage = function () {
    log ('Usage: node', process.argv[1], 'exchange'.green, 'symbol'.yellow, '[rateLimit]'.magenta)
    printSupportedExchanges ()
}

let printTicker = async (id, symbol, rateLimit = undefined) => {

    // check if the exchange is supported by ccxt
    let exchangeFound = ccxt.exchanges.indexOf (id) > -1
    if (exchangeFound) {

        log ('Instantiating', id.green, 'exchange')

        // instantiate the exchange by id
        let exchange = new ccxt[id] ()

        exchange.rateLimit = rateLimit ? rateLimit : exchange.rateLimit

        log.green ('Rate limit:', exchange.rateLimit.toString ().bright)

        // load all markets from the exchange
        let markets = await exchange.loadMarkets ()

        if (symbol in exchange.markets) {

            while (true) {

                const ticker = await exchange.fetchTicker (symbol)

                log ('--------------------------------------------------------')
                log (exchange.id.green, symbol.yellow, exchange.iso8601 (exchange.milliseconds ()))
                log (ccxt.omit (ticker, 'info'))
            }

        } else {

            log.error ('Symbol', symbol.bright, 'not found')
        }


    } else {

        log ('Exchange ' + id.red + ' not found')
        printSupportedExchanges ()
    }
}

;(async function main () {

    if (process.argv.length > 3) {

        const id = process.argv[2]
        const symbol = process.argv[3].toUpperCase ()
        const rateLimit = process.argv[4] ? parseInt (process.argv[4]) : undefined
        await printTicker (id, symbol, rateLimit)

    } else {

        printUsage ()
    }

    process.exit ()

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/live-ticker.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 48
- Comment lines: 3
- Blank lines: 29

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
node examples/js/live-ticker.js
```

