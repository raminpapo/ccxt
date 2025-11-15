# Documentation: js/src/test/Exchange/test.fetchTickers.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchTickers.js`
- **Size**: 2,753 bytes
- **Lines**: 48
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testTicker from './base/test.ticker.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchTickers(exchange, skippedProperties, symbol) {
    const withoutSymbol = testFetchTickersHelper(exchange, skippedProperties, undefined);
    const withSymbol = testFetchTickersHelper(exchange, skippedProperties, [symbol]);
    const results = await Promise.all([withoutSymbol, withSymbol]);
    testFetchTickersAmounts(exchange, skippedProperties, results[0]);
    return results;
}
async function testFetchTickersHelper(exchange, skippedProperties, argSymbols, argParams = {}) {
    const method = 'fetchTickers';
    const response = await exchange.fetchTickers(argSymbols, argParams);
    assert(typeof response === 'object', exchange.id + ' ' + method + ' ' + exchange.json(argSymbols) + ' must return an object. ' + exchange.json(response));
    const values = Object.values(response);
    let checkedSymbol = undefined;
    if (argSymbols !== undefined && argSymbols.length === 1) {
        checkedSymbol = argSymbols[0];
    }
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, values, checkedSymbol);
    for (let i = 0; i < values.length; i++) {
        // todo: symbol check here
        const ticker = values[i];
        testTicker(exchange, skippedProperties, method, ticker, checkedSymbol);
    }
    return response;
}
function testFetchTickersAmounts(exchange, skippedProperties, tickers) {
    const tickersValues = Object.values(tickers);
    if (!('checkActiveSymbols' in skippedProperties)) {
        //
        // ensure all "active" symbols have tickers
        //
        const nonInactiveMarkets = testSharedMethods.getActiveMarkets(exchange);
        const notInactiveSymbolsLength = nonInactiveMarkets.length;
        const obtainedTickersLength = tickersValues.length;
        const minRatio = 0.99; // 1.0 - 0.01 = 0.99, hardcoded to avoid C# transpiler type casting issues
        assert(obtainedTickersLength >= notInactiveSymbolsLength * minRatio, exchange.id + ' ' + 'fetchTickers' + ' must return tickers for all active markets. but returned: ' + obtainedTickersLength.toString() + ' tickers, ' + notInactiveSymbolsLength.toString() + ' active markets');
        //
        // ensure tickers length is less than markets length
        //
        const allMarkets = exchange.markets;
        const allMarketsLength = Object.keys(allMarkets).length;
        assert(obtainedTickersLength <= allMarketsLength, exchange.id + ' ' + 'fetchTickers' + ' must return <= than all markets, but returned: ' + obtainedTickersLength.toString() + ' tickers, ' + allMarketsLength.toString() + ' markets');
    }
}
export default testFetchTickers;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchTickers.js`.

**Functions defined**: testFetchTickersHelper, testFetchTickersAmounts, testFetchTickers

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 40
- Comment lines: 7
- Blank lines: 1

### Main Components

**Functions** (3):
- `testFetchTickers()`
- `testFetchTickersAmounts()`
- `testFetchTickersHelper()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.ticker.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `./base/test.ticker.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchTickers.js
```

