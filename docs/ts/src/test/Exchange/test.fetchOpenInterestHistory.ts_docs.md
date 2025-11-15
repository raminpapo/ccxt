# Documentation: ts/src/test/Exchange/test.fetchOpenInterestHistory.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchOpenInterestHistory.ts`
- **Size**: 761 bytes
- **Lines**: 17
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testOpenInterest from './base/test.openInterest.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchOpenInterestHistory (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchOpenInterestHistory';
    const openInterestHistory = await exchange.fetchOpenInterestHistory (symbol);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, openInterestHistory, symbol);
    for (let i = 0; i < openInterestHistory.length; i++) {
        testOpenInterest (exchange, skippedProperties, method, openInterestHistory[i]);
    }
    return true;
}

export default testFetchOpenInterestHistory;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchOpenInterestHistory.ts`.

**Functions defined**: testFetchOpenInterestHistory

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 14
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchOpenInterestHistory()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `./base/test.openInterest.js` (imported)
- `../../../ccxt` (imported)
- `assert` (imported)
- `./base/test.openInterest.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchOpenInterestHistory.ts
```

