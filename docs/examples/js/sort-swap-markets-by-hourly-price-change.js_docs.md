# Documentation: examples/js/sort-swap-markets-by-hourly-price-change.js

## File Metadata

- **Path**: `examples/js/sort-swap-markets-by-hourly-price-change.js`
- **Size**: 1,944 bytes
- **Lines**: 56
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../js/ccxt.js');

const exchange = new ccxt.binanceusdm ();
const timeframe = '1h';
const type = 'swap';

async function fetchOHLCV (symbol) {
    /**
     * @description Wrapper around exchange.fetchOHLCV method
     * @param {string} symbol CCXT unified symbol
     * @returns {[float|str]} 1d array with a single ohlcv record with the market symbol appended
     */
    try {
        const ohlcv = await exchange.fetchOHLCV (symbol, timeframe, undefined, 1);
        ohlcv[0].push (symbol);
        return ohlcv[0];
    } catch (err) {
        console.log (symbol + ' failed fetchOHLCV with error ' + err)
    }
}

function getPriceChangePercent (ohlcv) {
    /**
     * @description Gets the price change of a market as a percentage
     * @param {[float]} ohlcv A single ohlcv record with the market symbol appended
     * @returns {[float, str]} The price change as a percent with the symbol for the market
     */
    const open = ohlcv[1];
    const close = ohlcv[4];
    const symbol = ohlcv[6];
    const priceIncrease = close - open;
    const increaseAsRatio = priceIncrease / open;
    const increaseAsPercent = increaseAsRatio * 100;
    return [increaseAsPercent, symbol]
}

function sort (a, b) {
    return a[0] - b[0];
}

async function main () {
    /**
     * @description Gets the price change as a percent of every market matching type over the last timeframe matching timeframe and prints a sorted list. The most immediate candle is ignored because it is incomplete
     */
    await exchange.loadMarkets ();
    const allSwapSymbols = exchange.symbols.filter (symbol => exchange.market (symbol)[type] );
    const ohlcvs = await Promise.all (allSwapSymbols.map (symbol => fetchOHLCV (symbol)));
    const priceChanges = ohlcvs.map (ohlcv => getPriceChangePercent (ohlcv));
    const sorted = priceChanges.sort (sort);
    console.dir(sorted, {'maxArrayLength': null})
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/sort-swap-markets-by-hourly-price-change.js`.

**Functions defined**: getPriceChangePercent, main, sort, fetchOHLCV

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 48
- Comment lines: 13
- Blank lines: -5

### Main Components

**Functions** (4):
- `fetchOHLCV()`
- `getPriceChangePercent()`
- `main()`
- `sort()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/sort-swap-markets-by-hourly-price-change.js
```

