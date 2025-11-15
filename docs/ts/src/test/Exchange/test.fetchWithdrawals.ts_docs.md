# Documentation: ts/src/test/Exchange/test.fetchWithdrawals.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchWithdrawals.ts`
- **Size**: 846 bytes
- **Lines**: 19
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testDepositWithdrawal from './base/test.depositWithdrawal.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchWithdrawals (exchange: Exchange, skippedProperties: object, code: string) {
    const method = 'fetchWithdrawals';
    const transactions = await exchange.fetchWithdrawals (code);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, transactions, code);
    const now = exchange.milliseconds ();
    for (let i = 0; i < transactions.length; i++) {
        testDepositWithdrawal (exchange, skippedProperties, method, transactions[i], code, now);
    }
    testSharedMethods.assertTimestampOrder (exchange, method, code, transactions);
    return true;
}

export default testFetchWithdrawals;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchWithdrawals.ts`.

**Functions defined**: testFetchWithdrawals

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 16
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchWithdrawals()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.depositWithdrawal.js` (imported)
- `assert` (imported)
- `./base/test.depositWithdrawal.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchWithdrawals.ts
```

