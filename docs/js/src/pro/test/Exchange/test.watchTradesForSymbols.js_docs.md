# Documentation: js/src/pro/test/Exchange/test.watchTradesForSymbols.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchTradesForSymbols.js`
- **Size**: 1,611 bytes
- **Lines**: 39
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testTrade from '../../../test/Exchange/base/test.trade.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchTradesForSymbols(exchange, skippedProperties, symbols) {
    const method = 'watchTradesForSymbols';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        const success = true;
        try {
            response = await exchange.watchTradesForSymbols(symbols);
        }
        catch (e) {
            if (!testSharedMethods.isTemporaryFailure(e)) {
                throw e;
            }
            now = exchange.milliseconds();
            // continue;
        }
        if (success === true) {
            assert(Array.isArray(response), exchange.id + ' ' + method + ' ' + exchange.json(symbols) + ' must return an array. ' + exchange.json(response));
            now = exchange.milliseconds();
            let symbol = undefined;
            for (let i = 0; i < response.length; i++) {
                const trade = response[i];
                symbol = trade['symbol'];
                testTrade(exchange, skippedProperties, method, trade, symbol, now);
                testSharedMethods.assertInArray(exchange, skippedProperties, method, trade, 'symbol', symbols);
            }
            if (!('timestamp' in skippedProperties)) {
                testSharedMethods.assertTimestampOrder(exchange, method, symbol, response);
            }
        }
    }
    return true;
}
export default testWatchTradesForSymbols;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchTradesForSymbols.js`.

**Functions defined**: testWatchTradesForSymbols

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 37
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchTradesForSymbols()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.trade.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.trade.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchTradesForSymbols.js
```

