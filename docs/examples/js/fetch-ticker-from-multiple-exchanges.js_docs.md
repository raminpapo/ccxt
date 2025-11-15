# Documentation: examples/js/fetch-ticker-from-multiple-exchanges.js

## File Metadata

- **Path**: `examples/js/fetch-ticker-from-multiple-exchanges.js`
- **Size**: 746 bytes
- **Lines**: 35
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
(async () => {

    const exchanges = [
        'bittrex',
        'poloniex',
    ]

    const symbol = 'BTC/USDT'
    const tickers = {}

    await Promise.all (exchanges.map (exchangeId =>

        new Promise (async (resolve, reject) => {

            const exchange = new ccxt[exchangeId] ()

            while (true) {

                const ticker = await exchange.fetchTicker (symbol)
                tickers[exchangeId] = ticker

                Object.keys (tickers).map (exchangeId => {
                    const ticker = tickers[exchangeId]
                    console.log (ticker['datetime'], exchangeId, ticker['bid'], ticker['ask'])
                })
            }

        })

    ))

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-ticker-from-multiple-exchanges.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 22
- Comment lines: 0
- Blank lines: 13

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
node examples/js/fetch-ticker-from-multiple-exchanges.js
```

