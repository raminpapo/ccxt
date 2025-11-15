# Documentation: ts/src/test/Exchange/test.fetchL2OrderBook.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchL2OrderBook.ts`
- **Size**: 435 bytes
- **Lines**: 12
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
import testOrderBook from './base/test.orderBook.js';

async function testFetchL2OrderBook (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchL2OrderBook';
    const orderBook = await exchange.fetchL2OrderBook (symbol);
    testOrderBook (exchange, skippedProperties, method, orderBook, symbol);
    return true;
}

export default testFetchL2OrderBook;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchL2OrderBook.ts`.

**Functions defined**: testFetchL2OrderBook

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 9
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchL2OrderBook()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.orderBook.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.orderBook.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchL2OrderBook.ts
```

