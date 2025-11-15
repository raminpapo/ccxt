# Documentation: examples/js/tickers.js

## File Metadata

- **Path**: `examples/js/tickers.js`
- **Size**: 2,783 bytes
- **Lines**: 107
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import ansicolor from 'ansicolor';
import ololog from 'ololog';

const log = ololog.configure ({ locate: false }), verbose   = process.argv.includes ('--verbose');

ansicolor.nice

//-----------------------------------------------------------------------------

let printSupportedExchanges = function () {
    log ('Supported exchanges:', ccxt.exchanges.join (', ').green)
}

let printUsage = function () {
    log ('Usage: node', process.argv[1], 'id'.green, '[symbol]'.yellow)
    printSupportedExchanges ()
}

let printSymbols = function (exchange) {
    log (id.green, 'has', exchange.symbols.length, 'symbols:', exchange.symbols.join (', ').yellow)
}

let sleep = (ms) => new Promise (resolve => setTimeout (resolve, ms))

let printTicker = async (exchange, symbol) => {
    let ticker = await exchange.fetchTicker (symbol)
    log (exchange.id.green, symbol.yellow, 'ticker',
        ticker['datetime'],
        'high: '    + ticker['high'],
        'low: '     + ticker['low'],
        'bid: '     + ticker['bid'],
        'ask: '     + ticker['ask'],
        'volume: '  + ticker['baseVolume'])
    return ticker
}

//-----------------------------------------------------------------------------

let printTickers = async (id) => {

    log ('Instantiating', id.green, 'exchange exchange')

    // instantiate the exchange by id
    let exchange = new ccxt[id] ({ verbose })

    // load all markets from the exchange
    let markets = await exchange.loadMarkets ()

    if (process.argv.length > 3) { // if a symbol was supplied, get that symbol only

        let symbol = process.argv[3]

        await printTicker (exchange, symbol)

    } else { // otherwise run through all symbols one by one

        for (let symbol of exchange.symbols)
            if ((symbol.indexOf ('.d') < 0)) { // skip darkpool symbols

                const market = exchange.markets[symbol];

                if (!market['active']) {
                    log.red (exchange.id + ' ' + symbol + ' inactive');
                    continue;
                }

                await sleep (exchange.rateLimit)
                await printTicker (exchange, symbol)
            }
    }
}

//-----------------------------------------------------------------------------

;(async function main () {

    if (process.argv.length > 2) {

        let id = process.argv[2]

        // check if the exchange is supported by ccxt
        let exchangeFound = ccxt.exchanges.indexOf (id) > -1

        if (exchangeFound) {

            await printTickers (id)

        } else {

            log ('Exchange ' + id.red + ' not found')
            printUsage ()
        }

    } else {

        printUsage ()

    }

    process.exit ()

}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/tickers.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 107
- Code lines: 63
- Comment lines: 6
- Blank lines: 38

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
node examples/js/tickers.js
```

