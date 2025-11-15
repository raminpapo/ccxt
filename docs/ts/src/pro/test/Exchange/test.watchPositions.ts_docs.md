# Documentation: ts/src/pro/test/Exchange/test.watchPositions.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchPositions.ts`
- **Size**: 2,628 bytes
- **Lines**: 63
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import assert from 'assert';
import testPosition from '../../../test/Exchange/base/test.position.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { Exchange } from '../../../../ccxt.js';

async function testWatchPositions (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'watchPositions';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchPositions ([ symbol ]);
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
                testPosition (exchange, skippedProperties, method, response[i], undefined, now);
            }
            testSharedMethods.assertTimestampOrder (exchange, method, symbol, response);
        }

        //
        // Test with specific symbol
        //
        let positionsForSymbols = undefined;
        let success2 = true;
        try {
            positionsForSymbols = await exchange.watchPositions ([ symbol ]);
        } catch (e) {
            if (!testSharedMethods.isTemporaryFailure (e)) {
                throw e;
            }
            now = exchange.milliseconds ();
            // continue;
            success2 = false;
        }
        if (success2 === true) {
            assert (Array.isArray (positionsForSymbols), exchange.id + ' ' + method + ' must return an array, returned ' + exchange.json (positionsForSymbols));
            // max theoretical 4 positions: two for one-way-mode and two for two-way mode
            assert (positionsForSymbols.length <= 4, exchange.id + ' ' + method + ' positions length for particular symbol should be less than 4, returned ' + exchange.json (positionsForSymbols));
            now = exchange.milliseconds ();
            for (let i = 0; i < positionsForSymbols.length; i++) {
                testPosition (exchange, skippedProperties, method, positionsForSymbols[i], symbol, now);
            }
            testSharedMethods.assertTimestampOrder (exchange, method, symbol, positionsForSymbols);
        }
    }
    return true;
}

export default testWatchPositions;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchPositions.ts`.

**Functions defined**: testWatchPositions

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 52
- Comment lines: 6
- Blank lines: 5

### Main Components

**Functions** (1):
- `testWatchPositions()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.position.js` (imported)
- `../../../../ccxt.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.position.js` (referenced)
- `../../../../ccxt.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchPositions.ts
```

