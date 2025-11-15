# Documentation: js/src/test/Exchange/test.fetchLastPrices.d.ts

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchLastPrices.d.ts`
- **Size**: 197 bytes
- **Lines**: 4
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
declare function testFetchLastPrices(exchange: Exchange, skippedProperties: object, symbol: string): Promise<boolean>;
export default testFetchLastPrices;

```

## High-Level Overview

This is a TypeScript file located at `js/src/test/Exchange/test.fetchLastPrices.d.ts`.

**Functions defined**: testFetchLastPrices

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 4
- Code lines: 3
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchLastPrices()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../ccxt` (imported)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchLastPrices.d.ts
```

