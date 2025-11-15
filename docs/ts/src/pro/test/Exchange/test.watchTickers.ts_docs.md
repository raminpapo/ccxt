# Documentation: ts/src/pro/test/Exchange/test.watchTickers.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchTickers.ts`
- **Size**: 2,808 bytes
- **Lines**: 64
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import assert from 'assert';
import testTicker from '../../../test/Exchange/base/test.ticker.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { ArgumentsRequired } from '../../../base/errors.js';
import { Exchange, Tickers } from '../../../../ccxt.js';

async function testWatchTickers (exchange: Exchange, skippedProperties: object, symbol: string) {
    const withoutSymbol = testWatchTickersHelper (exchange, skippedProperties, undefined);
    const withSymbol = testWatchTickersHelper (exchange, skippedProperties, [ symbol ]);
    await Promise.all ([ withSymbol, withoutSymbol ]);
}

async function testWatchTickersHelper (exchange: Exchange, skippedProperties: object, argSymbols: string[], argParams = {}) {
    const method = 'watchTickers';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let response: Tickers = undefined;
        let success = true;
        let shouldReturn = false;
        try {
            response = await exchange.watchTickers (argSymbols, argParams);
        } catch (e) {
            // for some exchanges, specifically watchTickers method not subscribe
            // to "all tickers" itself, and it requires symbols to be set
            // so, in such case, if it's arguments-required exception, we don't
            // mark tests as failed, but just skip them
            if ((e instanceof ArgumentsRequired) && (argSymbols === undefined || argSymbols.length === 0)) {
                // todo: provide random symbols to try
                // return;
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
                const ticker = values[i];
                testTicker (exchange, skippedProperties, method, ticker, checkedSymbol);
            }
            now = exchange.milliseconds ();
        }
    }
    return true;
}

export default testWatchTickers;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchTickers.ts`.

**Functions defined**: testWatchTickersHelper, testWatchTickers

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 51
- Comment lines: 8
- Blank lines: 5

### Main Components

**Functions** (2):
- `testWatchTickers()`
- `testWatchTickersHelper()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/errors.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.ticker.js` (imported)
- `../../../base/errors.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../../ccxt.js` (referenced)
- `../../../test/Exchange/base/test.ticker.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchTickers.ts
```

