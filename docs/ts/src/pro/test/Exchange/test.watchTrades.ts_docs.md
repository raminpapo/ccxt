# Documentation: ts/src/pro/test/Exchange/test.watchTrades.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchTrades.ts`
- **Size**: 1,347 bytes
- **Lines**: 39
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import testTrade from '../../../test/Exchange/base/test.trade.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { Exchange } from '../../../../ccxt.js';


async function testWatchTrades (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'watchTrades';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchTrades (symbol);
        } catch (e) {
            if (!testSharedMethods.isTemporaryFailure (e)) {
                throw e;
            }
            now = exchange.milliseconds ();
            // continue;
            success = false;
        }
        if (success === true) {
            testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, response);
            now = exchange.milliseconds ();
            for (let i = 0; i < response.length; i++) {
                testTrade (exchange, skippedProperties, method, response[i], symbol, now);
            }
            if (!('timestampSort' in skippedProperties)) {
                testSharedMethods.assertTimestampOrder (exchange, method, symbol, response);
            }
        }

    }
}

export default testWatchTrades;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchTrades.ts`.

**Functions defined**: testWatchTrades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 32
- Comment lines: 1
- Blank lines: 6

### Main Components

**Functions** (1):
- `testWatchTrades()`



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
npm test ts/src/pro/test/Exchange/test.watchTrades.ts
```

