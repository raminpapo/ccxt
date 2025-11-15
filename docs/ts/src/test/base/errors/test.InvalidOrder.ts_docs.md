# Documentation: ts/src/test/base/errors/test.InvalidOrder.ts

## File Metadata

- **Path**: `ts/src/test/base/errors/test.InvalidOrder.ts`
- **Size**: 748 bytes
- **Lines**: 26
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// ----------------------------------------------------------------------------
// @ts-nocheck
import assert from 'assert';
import ccxt from '../../../ccxt.js';

// ----------------------------------------------------------------------------

export default async (exchange, symbol) => {
    if (!exchange.has.createOrder) {
        console.log ('createOrder() is not supported');
        return;
    }
    try {
        await exchange.createLimitBuyOrder (symbol, 0, 0);
        assert (false);
    } catch (e) {
        if (e instanceof ccxt.InvalidOrder) {
            console.log ('InvalidOrder thrown as expected');
        } else {
            console.log ('InvalidOrder failed, exception follows:');
            throw e;
        }
    }
};

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/errors/test.InvalidOrder.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 19
- Comment lines: 3
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/errors/test.InvalidOrder.ts
```

