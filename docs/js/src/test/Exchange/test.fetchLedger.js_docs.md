# Documentation: js/src/test/Exchange/test.fetchLedger.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchLedger.js`
- **Size**: 668 bytes
- **Lines**: 15
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testLedgerEntry from './base/test.ledgerEntry.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchLedger(exchange, skippedProperties, code) {
    const method = 'fetchLedger';
    const items = await exchange.fetchLedger(code);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, items, code);
    const now = exchange.milliseconds();
    for (let i = 0; i < items.length; i++) {
        testLedgerEntry(exchange, skippedProperties, method, items[i], code, now);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, code, items);
    return true;
}
export default testFetchLedger;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchLedger.js`.

**Functions defined**: testFetchLedger

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 14
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchLedger()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.ledgerEntry.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.ledgerEntry.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchLedger.js
```

