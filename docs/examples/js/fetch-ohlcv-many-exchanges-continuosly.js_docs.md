# Documentation: examples/js/fetch-ohlcv-many-exchanges-continuosly.js

## File Metadata

- **Path**: `examples/js/fetch-ohlcv-many-exchanges-continuosly.js`
- **Size**: 1,244 bytes
- **Lines**: 40
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
// fetch and handle constinuosly
async function fetchOHLCVContinuously(exchange, symbol) {
    while (true) {
        try {
            const ohlcv = await exchange.fetchOHLCV(symbol);
            const ohlcvLength = ohlcv.length;
            console.log('Fetched ', exchange.id, ' - ', symbol, ' candles. last candle: ', ohlcv[ohlcvLength - 1]);
        }
        catch (e) {
            console.log(e);
            break;
        }
    }
}
// start exchanges and fetch OHLCV loop
async function startExchange(exchangeName, symbols) {
    const ex = new ccxt[exchangeName]({});
    const promises = [];
    for (let i = 0; i < symbols.length; i++) {
        const symbol = symbols[i];
        promises.push(fetchOHLCVContinuously(ex, symbol));
    }
    await Promise.all(promises);
    await ex.close();
}
// main function
async function example() {
    const exchanges = ['binance', 'okx', 'kraken'];
    const symbols = ['BTC/USDT', 'ETH/USDT'];
    const promises = [];
    for (let i = 0; i < exchanges.length; i++) {
        const exchangeName = exchanges[i];
        promises.push(startExchange(exchangeName, symbols));
    }
    await Promise.all(promises);
}
await example();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-ohlcv-many-exchanges-continuosly.js`.

**Functions defined**: async, fetchOHLCVContinuously, example, startExchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 35
- Comment lines: 4
- Blank lines: 1

### Main Components

**Functions** (4):
- `async()`
- `example()`
- `fetchOHLCVContinuously()`
- `startExchange()`



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
node examples/js/fetch-ohlcv-many-exchanges-continuosly.js
```

