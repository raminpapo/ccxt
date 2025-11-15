# Documentation: ts/src/test/Exchange/test.fetchTicker.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchTicker.ts`
- **Size**: 400 bytes
- **Lines**: 12
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
import testTicker from './base/test.ticker.js';

async function testFetchTicker (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchTicker';
    const ticker = await exchange.fetchTicker (symbol);
    testTicker (exchange, skippedProperties, method, ticker, symbol);
    return true;
}

export default testFetchTicker;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchTicker.ts`.

**Functions defined**: testFetchTicker

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 9
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchTicker()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.ticker.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.ticker.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchTicker.ts
```

