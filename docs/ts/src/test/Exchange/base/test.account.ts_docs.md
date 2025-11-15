# Documentation: ts/src/test/Exchange/base/test.account.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.account.ts`
- **Size**: 709 bytes
- **Lines**: 18
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testAccount (exchange: Exchange, skippedProperties: object, method: string, entry: object) {
    const format = {
        'info': {},
        'code': 'BTC', // todo
        // 'name': 'account name', // todo
        'type': 'spot', // 'spot', 'margin', 'futures', 'swap'
        'id': '12345', // todo
    };
    const emptyAllowedFor = [ 'code', 'id' ];
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertCurrencyCode (exchange, skippedProperties, method, entry, entry['code']);
}

export default testAccount;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.account.ts`.

**Functions defined**: testAccount

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 14
- Comment lines: 1
- Blank lines: 3

### Main Components

**Functions** (1):
- `testAccount()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./test.sharedMethods.js` (imported)
- `../../../../ccxt` (imported)
- `./test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/base/test.account.ts
```

