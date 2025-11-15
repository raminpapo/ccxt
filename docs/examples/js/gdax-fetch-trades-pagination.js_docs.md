# Documentation: examples/js/gdax-fetch-trades-pagination.js

## File Metadata

- **Path**: `examples/js/gdax-fetch-trades-pagination.js`
- **Size**: 870 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
import ololog from 'ololog';

const { noLocate } = ololog;
const log = noLocate;

const exchange = new ccxt.coinbasepro ()

;(async () => {

    const symbol = 'ETH/BTC'
    const params = {}
    await exchange.loadMarkets ()
    while (true) {
        const trades = await exchange.fetchTrades (symbol, undefined, undefined, params)
        if (trades.length) {
            const firstTrade = trades[0]
            const lastTrade = trades[trades.length - 1]
            log.yellow ('Fetched', trades.length, symbol, 'trades from', firstTrade['datetime'], 'to', lastTrade['datetime'])
            if ('Cb-After' in exchange.last_response_headers) {
                params['after'] = exchange.last_response_headers['Cb-After'];
            }
        } else {
            log.green ('Done.')
            break;
        }
    }

}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/gdax-fetch-trades-pagination.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 24
- Comment lines: 0
- Blank lines: 6

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `ololog` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/gdax-fetch-trades-pagination.js
```

