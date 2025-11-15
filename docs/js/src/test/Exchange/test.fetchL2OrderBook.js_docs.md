# Documentation: js/src/test/Exchange/test.fetchL2OrderBook.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchL2OrderBook.js`
- **Size**: 362 bytes
- **Lines**: 9
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testOrderBook from './base/test.orderBook.js';
async function testFetchL2OrderBook(exchange, skippedProperties, symbol) {
    const method = 'fetchL2OrderBook';
    const orderBook = await exchange.fetchL2OrderBook(symbol);
    testOrderBook(exchange, skippedProperties, method, orderBook, symbol);
    return true;
}
export default testFetchL2OrderBook;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchL2OrderBook.js`.

**Functions defined**: testFetchL2OrderBook

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 9
- Code lines: 8
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchL2OrderBook()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.orderBook.js` (imported)
- `./base/test.orderBook.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchL2OrderBook.js
```

