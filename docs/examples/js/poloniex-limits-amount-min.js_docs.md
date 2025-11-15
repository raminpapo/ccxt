# Documentation: examples/js/poloniex-limits-amount-min.js

## File Metadata

- **Path**: `examples/js/poloniex-limits-amount-min.js`
- **Size**: 1,517 bytes
- **Lines**: 62
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
import fs from 'fs';
import ololog from 'ololog'

const log = ololog.configure.unlimited.noLocate,
      verbose = process.argv.includes ('--verbose'),
      keysGlobal = 'keys.json',
      keysLocal = 'keys.local.json',
      keysFile = fs.existsSync (keysLocal) ? keysLocal : (fs.existsSync (keysGlobal) ? keysGlobal : false),
      config = keysFile ? require ('../../' + keysFile) : {},
      exchange = new ccxt.poloniex (ccxt.extend ({
              enableRateLimit: true,
              verbose,
          }, config.poloniex || {}));(async () => {

    const test = async function (symbol) {

        try {

            await exchange.createOrder (symbol, 'limit', 'buy', 0, 0)

        } catch (e) {

            if (e instanceof ccxt.InvalidOrder) {

                const words = e.message.split (' ')
                let minAmount = parseFloat (words[words.length - 1])
                log.green ("'" + symbol + "': " + minAmount.toString () + ',')

            } else {

                throw e
            }
        }
    }

    await exchange.loadMarkets ()

    for (let i = 0; i < exchange.symbols.length; i++) {

        try {

            await test (exchange.symbols[i])

        } catch (e) {

            if (e instanceof ccxt.InvalidNonce) {

                log.yellow (e)

            } else {

                log.red (e)
                throw e
            }
        }


        await ccxt.sleep (5000) // sleep 5 seconds, no rush, safe delay
    }

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/poloniex-limits-amount-min.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 41
- Comment lines: 0
- Blank lines: 21

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `fs` (imported)
- `ololog` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/poloniex-limits-amount-min.js
```

