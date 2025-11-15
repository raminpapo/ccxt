# Documentation: ts/src/test/Exchange/test.fetchMarginModes.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchMarginModes.ts`
- **Size**: 1,062 bytes
- **Lines**: 21
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testMarginMode from './base/test.marginMode.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchMarginModes (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchMarginModes';
    const marginModes = await exchange.fetchMarginModes ([ 'symbol' ]);
    assert (typeof marginModes === 'object', exchange.id + ' ' + method + ' ' + symbol + ' must return an object. ' + exchange.json (marginModes));
    const marginModeKeys = Object.keys (marginModes);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, marginModes, symbol);
    for (let i = 0; i < marginModeKeys.length; i++) {
        const marginMode = marginModes[marginModeKeys[i]];
        testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, marginMode, symbol);
        testMarginMode (exchange, skippedProperties, method, marginMode);
    }
    return true;
}

export default testFetchMarginModes;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchMarginModes.ts`.

**Functions defined**: testFetchMarginModes

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 18
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchMarginModes()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.marginMode.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `assert` (imported)
- `./base/test.marginMode.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchMarginModes.ts
```

