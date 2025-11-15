# Documentation: ts/src/test/Exchange/test.fetchOpenOrders.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchOpenOrders.ts`
- **Size**: 923 bytes
- **Lines**: 21
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testOrder from './base/test.order.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchOpenOrders (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchOpenOrders';
    const orders = await exchange.fetchOpenOrders (symbol);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, orders, symbol);
    const now = exchange.milliseconds ();
    for (let i = 0; i < orders.length; i++) {
        const order = orders[i];
        testOrder (exchange, skippedProperties, method, order, symbol, now);
        testSharedMethods.assertInArray (exchange, skippedProperties, method, order, 'status', [ 'open' ]);
    }
    testSharedMethods.assertTimestampOrder (exchange, method, symbol, orders);
    return true;
}

export default testFetchOpenOrders;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchOpenOrders.ts`.

**Functions defined**: testFetchOpenOrders

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 18
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchOpenOrders()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.order.js` (imported)
- `assert` (imported)
- `./base/test.order.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchOpenOrders.ts
```

