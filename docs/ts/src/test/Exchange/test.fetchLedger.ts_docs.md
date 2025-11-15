# Documentation: ts/src/test/Exchange/test.fetchLedger.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchLedger.ts`
- **Size**: 773 bytes
- **Lines**: 19
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testLedgerEntry from './base/test.ledgerEntry.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchLedger (exchange: Exchange, skippedProperties: object, code: string) {
    const method = 'fetchLedger';
    const items = await exchange.fetchLedger (code);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, items, code);
    const now = exchange.milliseconds ();
    for (let i = 0; i < items.length; i++) {
        testLedgerEntry (exchange, skippedProperties, method, items[i], code, now);
    }
    testSharedMethods.assertTimestampOrder (exchange, method, code, items);
    return true;
}

export default testFetchLedger;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchLedger.ts`.

**Functions defined**: testFetchLedger

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 16
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchLedger()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.ledgerEntry.js` (imported)
- `assert` (imported)
- `./base/test.ledgerEntry.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchLedger.ts
```

