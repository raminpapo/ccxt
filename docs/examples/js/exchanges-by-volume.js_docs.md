# Documentation: examples/js/exchanges-by-volume.js

## File Metadata

- **Path**: `examples/js/exchanges-by-volume.js`
- **Size**: 1,358 bytes
- **Lines**: 60
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

(async () => {

    //     const exchanges = [
    //         'bittrex',
    //         'poloniex',
    //         'bitfinex'
    //     ]

    const exchanges = ccxt.exchanges

    const symbol = 'BTC/USDT'
    const tickers = {}
    const volumeField = 'baseVolume'

    console.log ('-----------------------------------------------------------')

    await Promise.all (exchanges.map (exchangeId =>

        new Promise (async (resolve, reject) => {

            try {

                const exchange = new ccxt[exchangeId] ()

                const ticker = await exchange.fetchTicker (symbol)

                if (ticker[volumeField] !== undefined) {
                    tickers[exchangeId] = ticker
                }

            } catch (e) {

                console.log (exchangeId, e.message.slice (0, 100))
            }

            resolve ()

        })

    ))

    console.log ('-----------------------------------------------------------')

    console.log (Object
        .keys (tickers)
        .sort ((a, b) =>
            ((tickers[a][volumeField] > tickers[b][volumeField]) ? 1 : ((tickers[a][volumeField] < tickers[b][volumeField]) ? -1 : 0)))
        .reverse ()
        .map (id => ({
            id,
            symbol,
            'volume': tickers[id][volumeField],
        }))
    )

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/exchanges-by-volume.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 34
- Comment lines: 5
- Blank lines: 21

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/exchanges-by-volume.js
```

