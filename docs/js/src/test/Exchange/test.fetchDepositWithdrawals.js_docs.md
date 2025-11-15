# Documentation: js/src/test/Exchange/test.fetchDepositWithdrawals.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchDepositWithdrawals.js`
- **Size**: 757 bytes
- **Lines**: 15
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testDepositWithdrawal from './base/test.depositWithdrawal.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchDepositWithdrawals(exchange, skippedProperties, code) {
    const method = 'fetchTransactions';
    const transactions = await exchange.fetchTransactions(code);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, transactions, code);
    const now = exchange.milliseconds();
    for (let i = 0; i < transactions.length; i++) {
        testDepositWithdrawal(exchange, skippedProperties, method, transactions[i], code, now);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, code, transactions);
    return true;
}
export default testFetchDepositWithdrawals;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchDepositWithdrawals.js`.

**Functions defined**: testFetchDepositWithdrawals

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 14
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchDepositWithdrawals()`



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
npm test js/src/test/Exchange/test.fetchDepositWithdrawals.js
```

