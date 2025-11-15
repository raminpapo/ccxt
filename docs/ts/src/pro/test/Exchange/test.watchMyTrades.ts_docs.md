# Documentation: ts/src/pro/test/Exchange/test.watchMyTrades.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchMyTrades.ts`
- **Size**: 1,301 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import testTrade from '../../../test/Exchange/base/test.trade.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { Exchange } from '../../../../ccxt.js';

async function testWatchMyTrades (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'watchMyTrades';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let success = true;
        let response = undefined;
        try {
            response = await exchange.watchMyTrades (symbol);
        } catch (e) {
            if (!testSharedMethods.isTemporaryFailure (e)) {
                throw e;
            }
            now = exchange.milliseconds ();
            // continue;
            success = false;
        }
        if (success === true) {
            testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, response, symbol);
            now = exchange.milliseconds ();
            for (let i = 0; i < response.length; i++) {
                testTrade (exchange, skippedProperties, method, response[i], symbol, now);
            }
            testSharedMethods.assertTimestampOrder (exchange, method, symbol, response);
        }
    }
    return true;
}

export default testWatchMyTrades;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchMyTrades.ts`.

**Functions defined**: testWatchMyTrades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 31
- Comment lines: 1
- Blank lines: 4

### Main Components

**Functions** (1):
- `testWatchMyTrades()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.trade.js` (imported)
- `../../../../ccxt.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../test/Exchange/base/test.trade.js` (referenced)
- `../../../../ccxt.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchMyTrades.ts
```

