# Documentation: js/src/pro/test/Exchange/test.watchTrades.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchTrades.js`
- **Size**: 1,267 bytes
- **Lines**: 34
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testTrade from '../../../test/Exchange/base/test.trade.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchTrades(exchange, skippedProperties, symbol) {
    const method = 'watchTrades';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchTrades(symbol);
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
            testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, response);
            now = exchange.milliseconds();
            for (let i = 0; i < response.length; i++) {
                testTrade(exchange, skippedProperties, method, response[i], symbol, now);
            }
            if (!('timestampSort' in skippedProperties)) {
                testSharedMethods.assertTimestampOrder(exchange, method, symbol, response);
            }
        }
    }
}
export default testWatchTrades;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchTrades.js`.

**Functions defined**: testWatchTrades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 32
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchTrades()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.trade.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../test/Exchange/base/test.trade.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchTrades.js
```

