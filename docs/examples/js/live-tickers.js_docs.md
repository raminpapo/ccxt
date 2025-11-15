# Documentation: examples/js/live-tickers.js

## File Metadata

- **Path**: `examples/js/live-tickers.js`
- **Size**: 2,004 bytes
- **Lines**: 74
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import asTable from 'as-table';
import ololog from 'ololog';
import ansicolor from 'ansicolor';
import ccxt from '../../js/ccxt.js';

ansicolor.nice

const { noLocate } = ololog;
const log = noLocate;

let printSupportedExchanges = function () {
    log ('Supported exchanges:', ccxt.exchanges.join (', ').green)
}

let printUsage = function () {
    log ('Usage: node', process.argv[1], 'exchange'.green)
    printSupportedExchanges ()
}

let printTickers = async (id) => {

    // check if the exchange is supported by ccxt
    let exchangeFound = ccxt.exchanges.indexOf (id) > -1
    if (exchangeFound) {

        log ('Instantiating', id.green, 'exchange')

        // instantiate the exchange by id
        let exchange = new ccxt[id] ()

        // load all markets from the exchange
        let markets = await exchange.loadMarkets ()

        while (true) {

            const tickers = await exchange.fetchTickers ()

            log ('--------------------------------------------------------')
            log (exchange.id.green, exchange.iso8601 (exchange.milliseconds ()))
            log ('Fetched', Object.values (tickers).length.toString ().green, 'tickers:')
            log (asTable.configure ({ delimiter: ' | '.dim, right: true }) (
                ccxt.sortBy (Object.values (tickers), 'quoteVolume', true)
                                   .slice (0,20)
                                   .map (ticker => ({
                                        symbol: ticker['symbol'],
                                        price: ticker['last'].toFixed (8),
                                        datetime: ticker['datetime'],
                                   }))))
        }

    } else {

        log ('Exchange ' + id.red + ' not found')
        printSupportedExchanges ()
    }
}

;(async function main () {

    if (process.argv.length > 2) {

        const id = process.argv[2]
        await printTickers (id)

    } else {

        printUsage ()
    }

    process.exit ()

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/live-tickers.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 74
- Code lines: 48
- Comment lines: 3
- Blank lines: 23

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
node examples/js/live-tickers.js
```

