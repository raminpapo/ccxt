# Documentation: js/src/pro/test/Exchange/test.watchOHLCVForSymbols.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchOHLCVForSymbols.js`
- **Size**: 2,466 bytes
- **Lines**: 50
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testOHLCV from '../../../test/Exchange/base/test.ohlcv.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchOHLCVForSymbols(exchange, skippedProperties, symbol) {
    const method = 'watchOHLCVForSymbols';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    const timeframeKeys = Object.keys(exchange.timeframes);
    assert(timeframeKeys.length, exchange.id + ' ' + method + ' - no timeframes found');
    // prefer 1m timeframe if available, otherwise return the first one
    let chosenTimeframeKey = '1m';
    if (!exchange.inArray(chosenTimeframeKey, timeframeKeys)) {
        chosenTimeframeKey = timeframeKeys[0];
    }
    const limit = 10;
    const duration = exchange.parseTimeframe(chosenTimeframeKey);
    const since = exchange.milliseconds() - duration * limit * 1000 - 1000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchOHLCVForSymbols([[symbol, chosenTimeframeKey]], since, limit);
        }
        catch (e) {
            if (!testSharedMethods.isTemporaryFailure(e)) {
                throw e;
            }
            now = exchange.milliseconds();
            // continue;
            success = false;
        }
        if (success === true) {
            const assertionMessage = exchange.id + ' ' + method + ' ' + symbol + ' ' + chosenTimeframeKey + ' | ' + exchange.json(response);
            assert(typeof response === 'object', 'Response must be a dictionary. ' + assertionMessage);
            assert(symbol in response, 'Response should contain the symbol as key. ' + assertionMessage);
            const symbolObj = response[symbol];
            assert(typeof symbolObj === 'object', 'Response.Symbol should be a dictionary. ' + assertionMessage);
            assert(chosenTimeframeKey in symbolObj, 'Response.symbol should contain the timeframe key. ' + assertionMessage);
            const ohlcvs = symbolObj[chosenTimeframeKey];
            assert(Array.isArray(ohlcvs), 'Response.symbol.timeframe should be an array. ' + assertionMessage);
            now = exchange.milliseconds();
            for (let i = 0; i < ohlcvs.length; i++) {
                testOHLCV(exchange, skippedProperties, method, ohlcvs[i], symbol, now);
            }
        }
    }
    return true;
}
export default testWatchOHLCVForSymbols;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchOHLCVForSymbols.js`.

**Functions defined**: testWatchOHLCVForSymbols

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 47
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchOHLCVForSymbols()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../test/Exchange/base/test.ohlcv.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../test/Exchange/base/test.ohlcv.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchOHLCVForSymbols.js
```

