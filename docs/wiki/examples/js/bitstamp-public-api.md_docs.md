# Documentation: wiki/examples/js/bitstamp-public-api.md

## File Metadata

- **Path**: `wiki/examples/js/bitstamp-public-api.md`
- **Size**: 1,375 bytes
- **Lines**: 44
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitstamp Public Api](./examples/js/)


 ```javascript
 
import ccxt from '../../js/ccxt.js';
import log from 'ololog';
import asTable from 'as-table';


const table = asTable.configure ({ delimiter: ' | ' }), id = 'bitstamp', exchange = new ccxt[id] ({ enableRateLimit: true }), symbol = 'BTC/USD';(async function main () {

    // Markets data
    const markets = await exchange.fetchMarkets ()
    console.log('Total number of markets: ', Object.keys(markets).length);

    // Currencies
    const currencies = await exchange.fetchCurrencies ()
    console.log('Currencies: ', JSON.stringify(currencies));

    // Order book data
    const orderbook = await exchange.fetchOrderBook (symbol)
    console.log ('Order book ', symbol, orderbook.asks[0], orderbook.bids[0])

    // Ticker
    const ticker = await exchange.fetchTicker (symbol)
    console.log ('Ticker ', symbol, " bid ", ticker.bid, " ask ", ticker.ask)

    // Trades
    const response = await exchange.fetchTrades (symbol, null, 10)
    log (table (response))

    // OHLC data
    const candles = await exchange.fetchOHLCV (symbol, '1m', undefined, 10);
    const first = candles[0]
    const last = candles[candles.length - 1]
    console.log (
        'Fetched', candles.length, symbol, 'candles',
        'from', exchange.iso8601 (first[0]),
        'to', exchange.iso8601 (last[0])
    )

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/bitstamp-public-api.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 26
- Comment lines: 6
- Blank lines: 12

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
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

