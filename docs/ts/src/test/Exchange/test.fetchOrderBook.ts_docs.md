# Documentation: ts/src/test/Exchange/test.fetchOrderBook.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchOrderBook.ts`
- **Size**: 427 bytes
- **Lines**: 12
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
import testOrderBook from './base/test.orderBook.js';

async function testFetchOrderBook (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchOrderBook';
    const orderbook = await exchange.fetchOrderBook (symbol);
    testOrderBook (exchange, skippedProperties, method, orderbook, symbol);
    return true;
}

export default testFetchOrderBook;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchOrderBook.ts`.

**Functions defined**: testFetchOrderBook

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 9
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchOrderBook()`



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
npm test ts/src/test/Exchange/test.fetchOrderBook.ts
```

