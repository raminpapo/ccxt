# Documentation: js/src/test/Exchange/test.fetchOpenOrders.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchOpenOrders.js`
- **Size**: 815 bytes
- **Lines**: 17
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testOrder from './base/test.order.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchOpenOrders(exchange, skippedProperties, symbol) {
    const method = 'fetchOpenOrders';
    const orders = await exchange.fetchOpenOrders(symbol);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, orders, symbol);
    const now = exchange.milliseconds();
    for (let i = 0; i < orders.length; i++) {
        const order = orders[i];
        testOrder(exchange, skippedProperties, method, order, symbol, now);
        testSharedMethods.assertInArray(exchange, skippedProperties, method, order, 'status', ['open']);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, symbol, orders);
    return true;
}
export default testFetchOpenOrders;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchOpenOrders.js`.

**Functions defined**: testFetchOpenOrders

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 16
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchOpenOrders()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.order.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.order.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchOpenOrders.js
```

