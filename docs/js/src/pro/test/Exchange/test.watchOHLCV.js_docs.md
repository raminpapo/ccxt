# Documentation: js/src/pro/test/Exchange/test.watchOHLCV.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchOHLCV.js`
- **Size**: 1,723 bytes
- **Lines**: 43
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testOHLCV from '../../../test/Exchange/base/test.ohlcv.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchOHLCV(exchange, skippedProperties, symbol) {
    const method = 'watchOHLCV';
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
            response = await exchange.watchOHLCV(symbol, chosenTimeframeKey, since, limit);
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
            testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, response, symbol);
            now = exchange.milliseconds();
            for (let i = 0; i < response.length; i++) {
                testOHLCV(exchange, skippedProperties, method, response[i], symbol, now);
            }
        }
    }
    return true;
}
export default testWatchOHLCV;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchOHLCV.js`.

**Functions defined**: testWatchOHLCV

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 40
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchOHLCV()`



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
npm test js/src/pro/test/Exchange/test.watchOHLCV.js
```

