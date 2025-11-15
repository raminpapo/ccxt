# Documentation: ts/src/test/Exchange/test.fetchOrders.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchOrders.ts`
- **Size**: 897 bytes
- **Lines**: 20
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testOrder from './base/test.order.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchOrders (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchOrders';
    const orders = await exchange.fetchOrders (symbol);
    assert (Array.isArray (orders), exchange.id + ' ' + method + ' must return an array, returned ' + exchange.json (orders));
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, orders, symbol);
    const now = exchange.milliseconds ();
    for (let i = 0; i < orders.length; i++) {
        testOrder (exchange, skippedProperties, method, orders[i], symbol, now);
    }
    testSharedMethods.assertTimestampOrder (exchange, method, symbol, orders);
    return true;
}

export default testFetchOrders;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchOrders.ts`.

**Functions defined**: testFetchOrders

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 17
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchOrders()`



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
npm test ts/src/test/Exchange/test.fetchOrders.ts
```

