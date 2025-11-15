# Documentation: js/src/test/Exchange/base/test.ohlcv.d.ts

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.ohlcv.d.ts`
- **Size**: 214 bytes
- **Lines**: 4
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
declare function testOHLCV(exchange: Exchange, skippedProperties: object, method: string, entry: number[], symbol: string, now: number): void;
export default testOHLCV;

```

## High-Level Overview

This is a TypeScript file located at `js/src/test/Exchange/base/test.ohlcv.d.ts`.

**Functions defined**: testOHLCV

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 4
- Code lines: 3
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testOHLCV()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../../ccxt` (imported)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/base/test.ohlcv.d.ts
```

