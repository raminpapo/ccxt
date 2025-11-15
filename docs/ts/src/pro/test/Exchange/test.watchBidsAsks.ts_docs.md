# Documentation: ts/src/pro/test/Exchange/test.watchBidsAsks.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchBidsAsks.ts`
- **Size**: 2,835 bytes
- **Lines**: 63
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import assert from 'assert';
import testTicker from '../../../test/Exchange/base/test.ticker.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { ArgumentsRequired } from '../../../base/errors.js';
import { Ticker } from '../../../base/types.js';
import { Exchange } from "../../../../ccxt";

async function testWatchBidsAsks (exchange: Exchange, skippedProperties: object, symbol: string) {
    const withoutSymbol = testWatchBidsAsksHelper (exchange, skippedProperties, undefined);
    const withSymbol = testWatchBidsAsksHelper (exchange, skippedProperties, [ symbol ]);
    await Promise.all ([ withSymbol, withoutSymbol ]);
}

async function testWatchBidsAsksHelper (exchange: Exchange, skippedProperties: object, argSymbols: string[], argParams = {}) {
    const method = 'watchBidsAsks';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let success = true;
        let shouldReturn = false;
        let response = undefined;
        try {
            response = await exchange.watchBidsAsks (argSymbols, argParams);
        } catch (e) {
            // for some exchanges, multi symbol methods might require symbols array to be present, so
            // so, if method throws "arguments-required" exception, we don't fail test, but just skip silently,
            // because tests will make a second call of this method with symbols array
            if ((e instanceof ArgumentsRequired) && (argSymbols === undefined || argSymbols.length === 0)) {
                // todo: provide random symbols to try
                // return false;
                shouldReturn = true;
            }
            else if (!testSharedMethods.isTemporaryFailure (e)) {
                throw e;
            }
            now = exchange.milliseconds ();
            // continue;
            success = false;
        }
        if (shouldReturn) {
            return false;
        }
        if (success === true) {
            assert (typeof response === 'object', exchange.id + ' ' + method + ' ' + exchange.json (argSymbols) + ' must return an object. ' + exchange.json (response));
            const values = Object.values (response);
            let checkedSymbol = undefined;
            if (argSymbols !== undefined && argSymbols.length === 1) {
                checkedSymbol = argSymbols[0];
            }
            testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, values, checkedSymbol);
            for (let i = 0; i < values.length; i++) {
                const ticker = values[i] as Ticker;
                testTicker (exchange, skippedProperties, method, ticker, checkedSymbol);
            }
            now = exchange.milliseconds ();
        }
    }
    return true;
}

export default testWatchBidsAsks;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchBidsAsks.ts`.

**Functions defined**: testWatchBidsAsksHelper, testWatchBidsAsks

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 52
- Comment lines: 6
- Blank lines: 5

### Main Components

**Functions** (2):
- `testWatchBidsAsks()`
- `testWatchBidsAsksHelper()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/errors.js` (imported)
- `../../../base/types.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../../ccxt` (imported)
- `../../../test/Exchange/base/test.ticker.js` (imported)
- `../../../base/errors.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../test/Exchange/base/test.ticker.js` (referenced)
- `../../../base/types.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchBidsAsks.ts
```

