# Documentation: ts/src/test/Exchange/test.fetchBorrowInterest.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchBorrowInterest.ts`
- **Size**: 759 bytes
- **Lines**: 17
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testBorrowInterest from './base/test.borrowInterest.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchBorrowInterest (exchange: Exchange, skippedProperties: object, code: string, symbol: string) {
    const method = 'fetchBorrowInterest';
    const borrowInterest = await exchange.fetchBorrowInterest (code, symbol);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, borrowInterest, code);
    for (let i = 0; i < borrowInterest.length; i++) {
        testBorrowInterest (exchange, skippedProperties, method, borrowInterest[i], code, symbol);
    }
    return true;
}

export default testFetchBorrowInterest;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchBorrowInterest.ts`.

**Functions defined**: testFetchBorrowInterest

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 14
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchBorrowInterest()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.borrowInterest.js` (imported)
- `assert` (imported)
- `./base/test.borrowInterest.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchBorrowInterest.ts
```

