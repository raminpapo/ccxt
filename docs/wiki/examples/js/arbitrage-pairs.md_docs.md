# Documentation: wiki/examples/js/arbitrage-pairs.md

## File Metadata

- **Path**: `wiki/examples/js/arbitrage-pairs.md`
- **Size**: 4,689 bytes
- **Lines**: 135
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Arbitrage Pairs](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import fs from 'fs';
import ansicolor from 'ansicolor';
import ololog from 'ololog';

const log = ololog.configure ({ locate: false }), verbose   = process.argv.includes ('--verbose'), keysGlobal = 'keys.json', keysLocal = 'keys.local.json', keysFile = fs.existsSync (keysLocal) ? keysLocal : (fs.existsSync (keysGlobal) ? keysGlobal : false), config = keysFile ? require ('../../' + keysFile) : {};

let printSupportedExchanges = function () {
    log ('Supported exchanges:', ccxt.exchanges.join (', ').green)
}

let printUsage = function () {
    log ('Usage: node', process.argv[1], 'id1'.green, 'id2'.yellow, 'id3'.blue, '...')
    printSupportedExchanges ()
}

let printExchangeSymbolsAndMarkets = function (exchange) {
    log (getExchangeSymbols (exchange))
    log (getExchangeMarketsTable (exchange))
}

let getExchangeMarketsTable = (exchange) => {
    return asTable.configure ({ delimiter: ' | ' }) (Object.values (markets))
}

let sleep = (ms) => new Promise (resolve => setTimeout (resolve, ms));

let proxies = [
    '', // no proxy by default
    'https://crossorigin.me/',
    'https://cors-anywhere.herokuapp.com/',
]

;(async function main () {

    if (process.argv.length > 3) {

        let ids = process.argv.slice (2)
        let exchanges = {}

        log (ids.join (', ').yellow)

        // load all markets from all exchanges
        for (let id of ids) {

            let settings = config[id] || {}

            // instantiate the exchange by id
            let exchange = new ccxt[id] (ccxt.extend ({
                // verbose,
                // 'proxy': 'https://cors-anywhere.herokuapp.com/',
            }, settings))

            // save it in a dictionary under its id for future use
            exchanges[id] = exchange

            // load all markets from the exchange
            let markets = await exchange.loadMarkets ()

            // basic round-robin proxy scheduler
            let currentProxy = 0
            let maxRetries   = proxies.length

            for (let numRetries = 0; numRetries < maxRetries; numRetries++) {

                try { // try to load exchange markets using current proxy

                    exchange.proxy = proxies[currentProxy]
                    await exchange.loadMarkets ()

                } catch (e) { // rotate proxies in case of connectivity errors, catch all other exceptions

                    // swallow connectivity exceptions only
                    if (e instanceof ccxt.DDoSProtection || e.message.includes ('ECONNRESET')) {
                        log.bright.yellow ('[DDoS Protection Error] ' + e.message)
                    } else if (e instanceof ccxt.RequestTimeout) {
                        log.bright.yellow ('[Timeout Error] ' + e.message)
                    } else if (e instanceof ccxt.AuthenticationError) {
                        log.bright.yellow ('[Authentication Error] ' + e.message)
                    } else if (e instanceof ccxt.ExchangeNotAvailable) {
                        log.bright.yellow ('[Exchange Not Available Error] ' + e.message)
                    } else if (e instanceof ccxt.ExchangeError) {
                        log.bright.yellow ('[Exchange Error] ' + e.message)
                    } else {
                        throw e; // rethrow all other exceptions
                    }

                    // retry next proxy in round-robin fashion in case of error
                    currentProxy = ++currentProxy % proxies.length
                }
            }

            log (id.green, 'loaded', exchange.symbols.length.toString ().green, 'markets')
        }

        log ('Loaded all markets'.green)

        // get all unique symbols
        let uniqueSymbols = ccxt.unique (ccxt.flatten (ids.map (id => exchanges[id].symbols)))

        // filter out symbols that are not present on at least two exchanges
        let arbitrableSymbols = uniqueSymbols
            .filter (symbol =>
                ids.filter (id =>
                    (exchanges[id].symbols.indexOf (symbol) >= 0)).length > 1)
            .sort ((id1, id2) => (id1 > id2) ? 1 : ((id2 > id1) ? -1 : 0))

        // print a table of arbitrable symbols
        let table = arbitrableSymbols.map (symbol => {
            let row = { symbol }
            for (let id of ids)
                if (exchanges[id].symbols.indexOf (symbol) >= 0)
                    row[id] = id
            return row
        })

        log (asTable.configure ({ delimiter: ' | ' }) (table))

    } else {

        printUsage ()

    }

    process.exit ()

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/arbitrage-pairs.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 135
- Code lines: 85
- Comment lines: 12
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

- `ansicolor` (imported)
- `ololog` (imported)
- `fs` (imported)
- `../../js/ccxt.js` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

