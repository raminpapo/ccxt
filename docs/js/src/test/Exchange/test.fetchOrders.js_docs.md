# Documentation: js/src/test/Exchange/test.fetchOrders.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchOrders.js`
- **Size**: 818 bytes
- **Lines**: 17
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testOrder from './base/test.order.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchOrders(exchange, skippedProperties, symbol) {
    const method = 'fetchOrders';
    const orders = await exchange.fetchOrders(symbol);
    assert(Array.isArray(orders), exchange.id + ' ' + method + ' must return an array, returned ' + exchange.json(orders));
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, orders, symbol);
    const now = exchange.milliseconds();
    for (let i = 0; i < orders.length; i++) {
        testOrder(exchange, skippedProperties, method, orders[i], symbol, now);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, symbol, orders);
    return true;
}
export default testFetchOrders;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchOrders.js`.

**Functions defined**: testFetchOrders

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 16
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchOrders()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `./base/test.order.js` (imported)
- `assert` (imported)
- `./base/test.order.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchOrders.js
```

