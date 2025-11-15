# Documentation: ts/src/test/Exchange/test.fetchBalance.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchBalance.ts`
- **Size**: 381 bytes
- **Lines**: 12
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
import testBalance from './base/test.balance.js';

async function testFetchBalance (exchange: Exchange, skippedProperties: object) {
    const method = 'fetchBalance';
    const response = await exchange.fetchBalance ();
    testBalance (exchange, skippedProperties, method, response);
    return true;
}

export default testFetchBalance;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchBalance.ts`.

**Functions defined**: testFetchBalance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 9
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchBalance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.balance.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.balance.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchBalance.ts
```

