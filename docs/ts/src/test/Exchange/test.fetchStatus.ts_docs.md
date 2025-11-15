# Documentation: ts/src/test/Exchange/test.fetchStatus.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchStatus.ts`
- **Size**: 396 bytes
- **Lines**: 12
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
import testStatus from './base/test.status.js';

async function testFetchStatus (exchange: Exchange, skippedProperties: object) {
    const method = 'fetchStatus';
    const status = await exchange.fetchStatus ();
    testStatus (exchange, skippedProperties, method, status, exchange.milliseconds ());
    return true;
}

export default testFetchStatus;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchStatus.ts`.

**Functions defined**: testFetchStatus

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 9
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchStatus()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.status.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.status.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchStatus.ts
```

