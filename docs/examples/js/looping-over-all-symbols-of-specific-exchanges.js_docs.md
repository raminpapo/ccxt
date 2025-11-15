# Documentation: examples/js/looping-over-all-symbols-of-specific-exchanges.js

## File Metadata

- **Path**: `examples/js/looping-over-all-symbols-of-specific-exchanges.js`
- **Size**: 1,743 bytes
- **Lines**: 62
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

;(async () => {

    const exchanges = [ 'bittrex', 'poloniex', 'hitbtc2' ]

    for (let exchangeId of exchanges) {

        // create the exchange instance
        const exchange = new ccxt[exchangeId] ()

        // preload all markets first, as explained in the Manual:
        // https://github.com/ccxt/ccxt/wiki/Manual#loading-markets

        // add error/exception handling as required by the Manual:
        // https://github.com/ccxt/ccxt/wiki/Manual#error-handling

        try {

            await exchange.loadMarkets ();

        } catch (e) {

            log.red ('Could not load markets from', exchange.id + ':', e.constructor.name, e.message)

            continue; // skip this exchange if markets failed to load

        }

        for (let symbol in exchange.markets) {

            console.log (exchange.id, symbol)

            // add error/exception handling as required by the Manual:
            // https://github.com/ccxt/ccxt/wiki/Manual#error-handling

            try { // try fetching the ticker for a symbol existing with that exchange

                const ticker = await exchange.fetchTicker (symbol)
                log.green (ticker)

            } catch (e) { // catch the error (if any) and handle it or ignore it

                log.red ('Could not fetch', symbol, 'ticker from', exchange.id + ':', e.constructor.name, e.message)

            }
        }
    }

}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/looping-over-all-symbols-of-specific-exchanges.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 27
- Comment lines: 8
- Blank lines: 27

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

**To execute this JavaScript file:**

```bash
node examples/js/looping-over-all-symbols-of-specific-exchanges.js
```

