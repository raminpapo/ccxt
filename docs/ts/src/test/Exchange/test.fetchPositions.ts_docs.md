# Documentation: ts/src/test/Exchange/test.fetchPositions.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchPositions.ts`
- **Size**: 1,650 bytes
- **Lines**: 29
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testPosition from './base/test.position.js';
import testSharedMethods from '../../test/Exchange/base/test.sharedMethods.js';

async function testFetchPositions (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchPositions';
    const now = exchange.milliseconds ();
    // without symbol
    const positions = await exchange.fetchPositions ();
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, positions, symbol);
    for (let i = 0; i < positions.length; i++) {
        testPosition (exchange, skippedProperties, method, positions[i], undefined, now);
    }
    // testSharedMethods.assertTimestampOrder (exchange, method, undefined, positions); // currently order of positions does not make sense
    // with symbol
    const positionsForSymbol = await exchange.fetchPositions ([ symbol ]);
    assert (Array.isArray (positionsForSymbol), exchange.id + ' ' + method + ' must return an array, returned ' + exchange.json (positionsForSymbol));
    const positionsForSymbolLength = positionsForSymbol.length;
    assert (positionsForSymbolLength <= 4, exchange.id + ' ' + method + ' positions length for particular symbol should be less than 4, returned ' + exchange.json (positionsForSymbol));
    for (let i = 0; i < positionsForSymbol.length; i++) {
        testPosition (exchange, skippedProperties, method, positionsForSymbol[i], symbol, now);
    }
    // testSharedMethods.assertTimestampOrder (exchange, method, symbol, positionsForSymbol);
    return true;
}

export default testFetchPositions;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchPositions.ts`.

**Functions defined**: testFetchPositions

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 22
- Comment lines: 4
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchPositions()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.position.js` (imported)
- `assert` (imported)
- `../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `./base/test.position.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchPositions.ts
```

