# Documentation: ts/src/test/Exchange/test.fetchLedgerEntry.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchLedgerEntry.ts`
- **Size**: 824 bytes
- **Lines**: 21
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
import testLedgerEntry from './base/test.ledgerEntry.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchLedgerEntry (exchange: Exchange, skippedProperties: object, code: string) {
    const method = 'fetchLedgerEntry';
    const items = await exchange.fetchLedger (code);
    const length = items.length;
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, items, code);
    if (length > 0) {
        const firstItem = items[0];
        const id = firstItem["id"];
        const item = await exchange.fetchLedgerEntry (id);
        const now = exchange.milliseconds ();
        testLedgerEntry (exchange, skippedProperties, method, item, code, now);
    }
    return true;
}

export default testFetchLedgerEntry;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchLedgerEntry.ts`.

**Functions defined**: testFetchLedgerEntry

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 18
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchLedgerEntry()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `./base/test.ledgerEntry.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.ledgerEntry.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchLedgerEntry.ts
```

