# Documentation: wiki/examples/js/fetch-ticker-from-multiple-exchanges.md

## File Metadata

- **Path**: `wiki/examples/js/fetch-ticker-from-multiple-exchanges.md`
- **Size**: 826 bytes
- **Lines**: 40
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Ticker From Multiple Exchanges](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/fetch-ticker-from-multiple-exchanges.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 25
- Comment lines: 0
- Blank lines: 15

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

**To execute this Markdown file:**

