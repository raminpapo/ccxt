# Documentation: examples/ccxt.pro/js/exchange-capabitities.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/exchange-capabitities.js`
- **Size**: 2,187 bytes
- **Lines**: 72
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
"use strict";

/*  ------------------------------------------------------------------------ */

const ccxt        = require ('../../../ccxt.js').pro
    , asTable     = require ('as-table') // .configure ({ print: require ('string.ify').noPretty })
    , log         = require ('ololog').noLocate
    , ansi        = require ('ansicolor').nice

;(async function test () {

    let total = 0
    let missing = 0
    let implemented = 0
    let emulated = 0

    const exchanges = ccxt.exchanges
        .map (id => new ccxt[id]())
        .filter (exchange => exchange.has.ws)

    log (
        asTable (
            exchanges
                .map (exchange => {

                    let result = {};

                    [
                        'ws',
                        'watchOrderBook',
                        'watchTicker',
                        'watchTrades',
                        'watchOHLCV',
                        'watchBalance',
                        'watchOrders',
                        'watchMyTrades',

                    ].forEach (key => {

                        total += 1

                        let capability = (key in exchange.has) ?
                            exchange.has[key].toString () :
                            'undefined'

                        if (!exchange.has[key]) {
                            capability = exchange.id.red.dim
                            missing += 1
                        } else if (exchange.has[key] === 'emulated') {
                            capability = exchange.id.yellow
                            emulated += 1
                        } else {
                            capability = exchange.id.green
                            implemented += 1
                        }

                        result[key] = capability
                    })

                    return result
                })
        )
    )

    log ('Summary:',
        exchanges.length.toString ().green, 'exchanges,',
        implemented.toString ().green, 'methods implemented,',
        emulated.toString ().yellow, 'emulated,',
        missing.toString ().red, 'missing,',
        total.toString (), 'total')

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/exchange-capabitities.js`.

**Functions defined**: test

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 56
- Comment lines: 1
- Blank lines: 15

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/ccxt.pro/js/exchange-capabitities.js
```

