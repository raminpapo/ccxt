# Documentation: js/src/test/Exchange/test.fetchOpenInterestHistory.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchOpenInterestHistory.js`
- **Size**: 658 bytes
- **Lines**: 13
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testOpenInterest from './base/test.openInterest.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchOpenInterestHistory(exchange, skippedProperties, symbol) {
    const method = 'fetchOpenInterestHistory';
    const openInterestHistory = await exchange.fetchOpenInterestHistory(symbol);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, openInterestHistory, symbol);
    for (let i = 0; i < openInterestHistory.length; i++) {
        testOpenInterest(exchange, skippedProperties, method, openInterestHistory[i]);
    }
    return true;
}
export default testFetchOpenInterestHistory;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchOpenInterestHistory.js`.

**Functions defined**: testFetchOpenInterestHistory

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 12
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchOpenInterestHistory()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.openInterest.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.openInterest.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchOpenInterestHistory.js
```

