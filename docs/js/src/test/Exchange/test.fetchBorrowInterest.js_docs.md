# Documentation: js/src/test/Exchange/test.fetchBorrowInterest.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchBorrowInterest.js`
- **Size**: 648 bytes
- **Lines**: 13
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testBorrowInterest from './base/test.borrowInterest.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchBorrowInterest(exchange, skippedProperties, code, symbol) {
    const method = 'fetchBorrowInterest';
    const borrowInterest = await exchange.fetchBorrowInterest(code, symbol);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, borrowInterest, code);
    for (let i = 0; i < borrowInterest.length; i++) {
        testBorrowInterest(exchange, skippedProperties, method, borrowInterest[i], code, symbol);
    }
    return true;
}
export default testFetchBorrowInterest;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchBorrowInterest.js`.

**Functions defined**: testFetchBorrowInterest

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 12
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchBorrowInterest()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.borrowInterest.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.borrowInterest.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchBorrowInterest.js
```

