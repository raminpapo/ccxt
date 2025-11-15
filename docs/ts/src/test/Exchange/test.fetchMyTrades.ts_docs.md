# Documentation: ts/src/test/Exchange/test.fetchMyTrades.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchMyTrades.ts`
- **Size**: 778 bytes
- **Lines**: 19
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testSharedMethods from './base/test.sharedMethods.js';
import testTrade from './base/test.trade.js';

async function testFetchMyTrades (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchMyTrades';
    const trades = await exchange.fetchMyTrades (symbol);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, trades, symbol);
    const now = exchange.milliseconds ();
    for (let i = 0; i < trades.length; i++) {
        testTrade (exchange, skippedProperties, method, trades[i], symbol, now);
    }
    testSharedMethods.assertTimestampOrder (exchange, method, symbol, trades);
    return true;
}

export default testFetchMyTrades;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchMyTrades.ts`.

**Functions defined**: testFetchMyTrades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 16
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchMyTrades()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.trade.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `assert` (imported)
- `./base/test.trade.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchMyTrades.ts
```

