# Documentation: ts/src/pro/test/Exchange/test.watchTradesForSymbols.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchTradesForSymbols.ts`
- **Size**: 1,695 bytes
- **Lines**: 42
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import assert from 'assert';
import testTrade from '../../../test/Exchange/base/test.trade.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { Exchange } from '../../../../ccxt.js';

async function testWatchTradesForSymbols (exchange: Exchange, skippedProperties: object, symbols: string[]) {
    const method = 'watchTradesForSymbols';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        const success = true;
        try {
            response = await exchange.watchTradesForSymbols (symbols);
        } catch (e) {
            if (!testSharedMethods.isTemporaryFailure (e)) {
                throw e;
            }
            now = exchange.milliseconds ();
            // continue;
        }
        if (success === true) {
            assert (Array.isArray (response), exchange.id + ' ' + method + ' ' + exchange.json (symbols) + ' must return an array. ' + exchange.json (response));
            now = exchange.milliseconds ();
            let symbol = undefined;
            for (let i = 0; i < response.length; i++) {
                const trade = response[i];
                symbol = trade['symbol'];
                testTrade (exchange, skippedProperties, method, trade, symbol, now);
                testSharedMethods.assertInArray (exchange, skippedProperties, method, trade, 'symbol', symbols);
            }
            if (!('timestamp' in skippedProperties)) {
                testSharedMethods.assertTimestampOrder (exchange, method, symbol, response);
            }
        }
    }
    return true;
}

export default testWatchTradesForSymbols;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchTradesForSymbols.ts`.

**Functions defined**: testWatchTradesForSymbols

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 37
- Comment lines: 1
- Blank lines: 4

### Main Components

**Functions** (1):
- `testWatchTradesForSymbols()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.trade.js` (imported)
- `../../../../ccxt.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.trade.js` (referenced)
- `../../../../ccxt.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchTradesForSymbols.ts
```

