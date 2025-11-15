# Documentation: js/src/pro/test/Exchange/test.watchMyTrades.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchMyTrades.js`
- **Size**: 1,223 bytes
- **Lines**: 33
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testTrade from '../../../test/Exchange/base/test.trade.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchMyTrades(exchange, skippedProperties, symbol) {
    const method = 'watchMyTrades';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let success = true;
        let response = undefined;
        try {
            response = await exchange.watchMyTrades(symbol);
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
                testTrade(exchange, skippedProperties, method, response[i], symbol, now);
            }
            testSharedMethods.assertTimestampOrder(exchange, method, symbol, response);
        }
    }
    return true;
}
export default testWatchMyTrades;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchMyTrades.js`.

**Functions defined**: testWatchMyTrades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 31
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchMyTrades()`



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
npm test js/src/pro/test/Exchange/test.watchMyTrades.js
```

