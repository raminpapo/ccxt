# Documentation: ts/src/test/Exchange/test.fetchAccounts.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchAccounts.ts`
- **Size**: 628 bytes
- **Lines**: 17
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testAccount from './base/test.account.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchAccounts (exchange: Exchange, skippedProperties: object) {
    const method = 'fetchAccounts';
    const accounts = await exchange.fetchAccounts ();
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, accounts);
    for (let i = 0; i < accounts.length; i++) {
        testAccount (exchange, skippedProperties, method, accounts[i]);
    }
    return true;
}

export default testFetchAccounts;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchAccounts.ts`.

**Functions defined**: testFetchAccounts

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 14
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchAccounts()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.account.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `assert` (imported)
- `./base/test.account.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchAccounts.ts
```

