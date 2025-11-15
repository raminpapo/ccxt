# Documentation: js/src/test/Exchange/test.fetchOrderBooks.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchOrderBooks.js`
- **Size**: 820 bytes
- **Lines**: 17
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testOrderBook from './base/test.orderBook.js';
async function testFetchOrderBooks(exchange, skippedProperties) {
    const method = 'fetchOrderBooks';
    const symbol = exchange.symbols[0];
    const orderBooks = await exchange.fetchOrderBooks([symbol]);
    assert(typeof orderBooks === 'object', exchange.id + ' ' + method + ' must return an object. ' + exchange.json(orderBooks));
    const orderBookKeys = Object.keys(orderBooks);
    assert(orderBookKeys.length, exchange.id + ' ' + method + ' returned 0 length data');
    for (let i = 0; i < orderBookKeys.length; i++) {
        const symbolInner = orderBookKeys[i];
        testOrderBook(exchange, skippedProperties, method, orderBooks[symbolInner], symbolInner);
    }
    return true;
}
export default testFetchOrderBooks;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchOrderBooks.js`.

**Functions defined**: testFetchOrderBooks

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 16
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchOrderBooks()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.orderBook.js` (imported)
- `assert` (imported)
- `./base/test.orderBook.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchOrderBooks.js
```

