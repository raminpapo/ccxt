# Documentation: examples/js/fetch-ticker-where-available.js

## File Metadata

- **Path**: `examples/js/fetch-ticker-where-available.js`
- **Size**: 1,712 bytes
- **Lines**: 75
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import asTable from 'as-table';
import log from 'ololog';
import ansicolor from 'ansicolor';


ansicolor.nice

let printUsage = function () {
    log ('Usage: node', process.argv[1], 'symbol'.green)
}

;(async function main () {

    if (process.argv.length > 2) {

        let symbol = process.argv[2].toUpperCase ()

        for (let i = 0; i < ccxt.exchanges.length; i++) {

            let id = ccxt.exchanges[i]

            const exchange = new ccxt[id] ()
            if (exchange.has.fetchTicker) {

                try {

                    await exchange.loadMarkets ()

                    if (exchange.symbols.includes (symbol)) {

                        log (id.green)

                        const ticker = await exchange.fetchTicker (symbol)

                        log.dim (ticker)

                        if (ticker['baseVolume'] && ticker['quoteVolume']) {

                            if (ticker['bid'] > 1) {

                                if (ticker['baseVolume'] > ticker['quoteVolume'])
                                log (id.bright, 'baseVolume > quoteVolume ← !'.bright)

                            } else {

                                if (ticker['baseVolume'] < ticker['quoteVolume'])
                                    log (id.bright, 'baseVolume < quoteVolume ← !'.bright)

                            }

                        }

                    } else {

                        log (id.yellow)
                    }

                } catch (e) {

                    log.error (id.red, e.toString ().red)
                }
            }
        }

    } else {

        printUsage ()
    }

    process.exit ()

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-ticker-where-available.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 43
- Comment lines: 0
- Blank lines: 32

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
node examples/js/fetch-ticker-where-available.js
```

