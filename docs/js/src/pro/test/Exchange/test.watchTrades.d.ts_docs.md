# Documentation: js/src/pro/test/Exchange/test.watchTrades.d.ts

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchTrades.d.ts`
- **Size**: 192 bytes
- **Lines**: 4
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from '../../../../ccxt.js';
declare function testWatchTrades(exchange: Exchange, skippedProperties: object, symbol: string): Promise<void>;
export default testWatchTrades;

```

## High-Level Overview

This is a TypeScript file located at `js/src/pro/test/Exchange/test.watchTrades.d.ts`.

**Functions defined**: testWatchTrades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 4
- Code lines: 3
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchTrades()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../../ccxt.js` (imported)
- `../../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchTrades.d.ts
```

