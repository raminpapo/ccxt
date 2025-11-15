# Documentation: ts/src/pro/test/Exchange/test.watchLiquidationsForSymbols.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchLiquidationsForSymbols.ts`
- **Size**: 1,677 bytes
- **Lines**: 63
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../../ccxt";
import { NetworkError } from '../../../base/errors.js';
import testLiquidation from '../../../test/Exchange/base/test.liquidation.js';


async function testWatchLiquidationsForSymbols (exchange: Exchange, skippedProperties: object, symbol: string) {

    const method = 'watchLiquidationsForSymbols';

    // we have to skip some exchanges here due to the frequency of trading
    const skippedExchanges = [];

    if (exchange.inArray (exchange.id, skippedExchanges)) {
        console.log (exchange.id, method + '() test skipped');
        return false;
    }

    if (!exchange.has[method]) {
        console.log (exchange.id, method + '() is not supported');
        return false;
    }

    let response = undefined;

    let now = Date.now ();
    const ends = now + 10000;

    while (now < ends) {

        try {

            response = await exchange[method] ([ symbol ]);

            now = Date.now ();

            const isArray = Array.isArray (response);
            assert (isArray, "response must be an array");

            console.log (exchange.iso8601 (now), exchange.id, symbol, method, Object.values (response).length, 'liquidations');

            // log.noLocate (asTable (response))

            for (let i = 0; i < response.length; i++) {
                testLiquidation (exchange, skippedProperties, method, response[i], symbol);
            }

        } catch (e) {

            if (!(e instanceof NetworkError)) {
                throw e;
            }

            now = Date.now ();
        }

    }

    return response;
}

export default testWatchLiquidationsForSymbols;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchLiquidationsForSymbols.ts`.

**Functions defined**: testWatchLiquidationsForSymbols

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 38
- Comment lines: 2
- Blank lines: 23

### Main Components

**Functions** (1):
- `testWatchLiquidationsForSymbols()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/errors.js` (imported)
- `../../../test/Exchange/base/test.liquidation.js` (imported)
- `../../../../ccxt` (imported)
- `assert` (imported)
- `../../../base/errors.js` (referenced)
- `../../../test/Exchange/base/test.liquidation.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchLiquidationsForSymbols.ts
```

