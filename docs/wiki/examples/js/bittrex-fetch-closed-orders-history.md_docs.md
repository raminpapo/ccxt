# Documentation: wiki/examples/js/bittrex-fetch-closed-orders-history.md

## File Metadata

- **Path**: `wiki/examples/js/bittrex-fetch-closed-orders-history.md`
- **Size**: 1,863 bytes
- **Lines**: 75
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bittrex Fetch Closed Orders History](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';
import ololog from 'ololog';
import asTable from 'as-table';


const { noLocate } = ololog;
const log = noLocate;

const exchange = new ccxt.bittrex ({
        'enableRateLimit': true,
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET',
    });(async () => {

    await exchange.loadMarkets ()

    const symbol = 'ETH/BTC'
        , market = exchange.markets[symbol]
        , startingDate = '2017-01-01T00:00:00'
        , now = exchange.milliseconds ()

    log.bright.green ('\nFetching history for:', symbol, '\n')

    let allOrders = []
    let since = exchange.parse8601 (startingDate)

    while (since < now) {

        try {

            log.bright.blue ('Fetching history for', symbol, 'since', exchange.iso8601 (since))
            const orders = await exchange.fetchClosedOrders (symbol, since)
            log.green.dim ('Fetched', orders.length, 'orders')

            allOrders = allOrders.concat (orders)

            if (orders.length) {

                const lastOrder = orders[orders.length - 1]
                since = lastOrder['timestamp'] + 1

            } else {

                break // no more orders left for this symbol, move to next one
            }

        } catch (e) {

            log.red.unlimited (e)

        }
    }

    // omit the following keys for a compact table output
    // otherwise it won't fit into the screen width
    const omittedKeys = [
        'info',
        'timestamp',
        'lastTradeTimestamp',
        'fee',
    ]

    log.yellow (asTable (allOrders.map (order => exchange.omit (order, omittedKeys))))
    log.green ('Fetched', allOrders.length, symbol, 'orders in total')

    // do whatever you want to do with them, calculate profit loss, etc...

}) ()

 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/bittrex-fetch-closed-orders-history.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 46
- Comment lines: 3
- Blank lines: 26

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `ololog` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

