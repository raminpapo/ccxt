# Documentation: ts/src/test/Exchange/test.fetchLiquidations.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchLiquidations.ts`
- **Size**: 903 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testSharedMethods from './base/test.sharedMethods.js';
import testLiquidation from './base/test.liquidation.js';

async function testFetchLiquidations (exchange: Exchange, skippedProperties: object, code: string) {
    const method = 'fetchLiquidations';
    if (!exchange.has['fetchLiquidations']) {
        return true;
    }
    const items = await exchange.fetchLiquidations (code);
    assert (Array.isArray (items), exchange.id + ' ' + method + ' ' + code + ' must return an array. ' + exchange.json (items));
    // const now = exchange.milliseconds ();
    for (let i = 0; i < items.length; i++) {
        testLiquidation (exchange, skippedProperties, method, items[i], code);
    }
    testSharedMethods.assertTimestampOrder (exchange, method, code, items);
    return true;
}

export default testFetchLiquidations;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchLiquidations.ts`.

**Functions defined**: testFetchLiquidations

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 18
- Comment lines: 1
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchLiquidations()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.liquidation.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `assert` (imported)
- `./base/test.liquidation.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchLiquidations.ts
```

