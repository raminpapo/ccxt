# Documentation: ts/src/pro/test/Exchange/test.watchPosition.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchPosition.ts`
- **Size**: 1,219 bytes
- **Lines**: 34
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import assert from 'assert';
import testPosition from '../../../test/Exchange/base/test.position.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { Exchange } from '../../../../ccxt.js';

async function testWatchPosition (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'watchPosition';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchPosition (symbol);
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
            testPosition (exchange, skippedProperties, method, response, undefined, now);
        }
    }
    return true;
}

export default testWatchPosition;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchPosition.ts`.

**Functions defined**: testWatchPosition

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 29
- Comment lines: 1
- Blank lines: 4

### Main Components

**Functions** (1):
- `testWatchPosition()`



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
npm test ts/src/pro/test/Exchange/test.watchPosition.ts
```

