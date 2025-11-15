# Documentation: js/src/pro/test/Exchange/test.watchOrders.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchOrders.js`
- **Size**: 1,215 bytes
- **Lines**: 33
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testOrder from '../../../test/Exchange/base/test.order.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchOrders(exchange, skippedProperties, symbol) {
    const method = 'watchOrders';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchOrders(symbol);
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
                testOrder(exchange, skippedProperties, method, response[i], symbol, now);
            }
            testSharedMethods.assertTimestampOrder(exchange, method, symbol, response);
        }
    }
    return true;
}
export default testWatchOrders;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchOrders.js`.

**Functions defined**: testWatchOrders

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 31
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchOrders()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../test/Exchange/base/test.order.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../test/Exchange/base/test.order.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchOrders.js
```

