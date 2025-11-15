# Documentation: ts/src/test/Exchange/test.fetchLastPrices.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchLastPrices.ts`
- **Size**: 1,466 bytes
- **Lines**: 32
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testLastPrice from './base/test.lastPrice.js';
import testSharedMethods from './base/test.sharedMethods.js';
import { LastPrices } from '../../base/types';

async function testFetchLastPrices (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchLastprices';
    // log ('fetching all tickers at once...')
    let response: LastPrices = undefined;
    let checkedSymbol = undefined;
    try {
        response = await exchange.fetchLastPrices ();
    } catch (e) {
        response = await exchange.fetchLastPrices ([ symbol ]);
        checkedSymbol = symbol;
    }
    assert (typeof response === 'object', exchange.id + ' ' + method + ' ' + checkedSymbol + ' must return an object. ' + exchange.json (response));
    const values = Object.values (response);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, values, checkedSymbol);
    let atLeastOnePassed = false;
    for (let i = 0; i < values.length; i++) {
        // todo: symbol check here
        testLastPrice (exchange, skippedProperties, method, values[i], checkedSymbol);
        atLeastOnePassed = atLeastOnePassed || (exchange.safeNumber (values[i], 'price') > 0);
    }
    assert (atLeastOnePassed, exchange.id + ' ' + method + ' ' + checkedSymbol + ' at least one symbol should pass the test');
    return true;
}

export default testFetchLastPrices;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchLastPrices.ts`.

**Functions defined**: testFetchLastPrices

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 27
- Comment lines: 2
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchLastPrices()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../base/types` (imported)
- `assert` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.lastPrice.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.lastPrice.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchLastPrices.ts
```

