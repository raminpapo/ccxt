# Documentation: ts/src/pro/test/Exchange/test.watchLiquidations.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchLiquidations.ts`
- **Size**: 1,783 bytes
- **Lines**: 64
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import assert from 'assert';
import { Exchange } from "../../../../ccxt";
import testLiquidation from '../../../test/Exchange/base/test.liquidation.js';
import { NetworkError } from '../../../base/errors.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';


async function testWatchLiquidations (exchange: Exchange, skippedProperties: object, symbol: string) {

    // log (symbol.green, 'watching trades...')

    const method = 'watchLiquidations';

    // we have to skip some exchanges here due to the frequency of trading
    const skippedExchanges = [];

    if (exchange.inArray (exchange.id, skippedExchanges)) {
        console.log (exchange.id, method + '() test skipped');
        return false;
    }

    if (!exchange.has[method]) {
        console.log (exchange.id, 'does not support', method + '() method');
        return false;
    }

    let response = undefined;

    let now = Date.now ();
    const ends = now + 10000;

    while (now < ends) {

        try {

            response = await exchange[method] (symbol);

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
export default testWatchLiquidations;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchLiquidations.ts`.

**Functions defined**: testWatchLiquidations

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 39
- Comment lines: 3
- Blank lines: 22

### Main Components

**Functions** (1):
- `testWatchLiquidations()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/errors.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.liquidation.js` (imported)
- `../../../../ccxt` (imported)
- `../../../base/errors.js` (referenced)
- `../../../test/Exchange/base/test.liquidation.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchLiquidations.ts
```

