# Documentation: ts/src/pro/test/Exchange/test.watchTicker.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchTicker.ts`
- **Size**: 1,197 bytes
- **Lines**: 34
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import assert from 'assert';
import testTicker from '../../../test/Exchange/base/test.ticker.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { Exchange } from '../../../../ccxt.js';

async function testWatchTicker (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'watchTicker';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchTicker (symbol);
        } catch (e) {
            if (!testSharedMethods.isTemporaryFailure (e)) {
                throw e;
            }
            now = exchange.milliseconds ();
            // continue;
            success = false;
        }
        if (success === true) {
            assert (typeof response === 'object', exchange.id + ' ' + method + ' ' + symbol + ' must return an object. ' + exchange.json (response));
            now = exchange.milliseconds ();
            testTicker (exchange, skippedProperties, method, response, symbol);
        }
    }
    return true;
}

export default testWatchTicker;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchTicker.ts`.

**Functions defined**: testWatchTicker

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 29
- Comment lines: 1
- Blank lines: 4

### Main Components

**Functions** (1):
- `testWatchTicker()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../../ccxt.js` (imported)
- `../../../test/Exchange/base/test.ticker.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../../ccxt.js` (referenced)
- `../../../test/Exchange/base/test.ticker.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchTicker.ts
```

