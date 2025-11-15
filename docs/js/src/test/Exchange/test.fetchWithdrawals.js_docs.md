# Documentation: js/src/test/Exchange/test.fetchWithdrawals.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchWithdrawals.js`
- **Size**: 741 bytes
- **Lines**: 15
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testDepositWithdrawal from './base/test.depositWithdrawal.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchWithdrawals(exchange, skippedProperties, code) {
    const method = 'fetchWithdrawals';
    const transactions = await exchange.fetchWithdrawals(code);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, transactions, code);
    const now = exchange.milliseconds();
    for (let i = 0; i < transactions.length; i++) {
        testDepositWithdrawal(exchange, skippedProperties, method, transactions[i], code, now);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, code, transactions);
    return true;
}
export default testFetchWithdrawals;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchWithdrawals.js`.

**Functions defined**: testFetchWithdrawals

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 14
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchWithdrawals()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.depositWithdrawal.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.depositWithdrawal.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchWithdrawals.js
```

