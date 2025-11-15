# Documentation: ts/src/test/base/errors/test.OrderNotFound.ts

## File Metadata

- **Path**: `ts/src/test/base/errors/test.OrderNotFound.ts`
- **Size**: 781 bytes
- **Lines**: 28
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
    const id = 1;
    try {
        await exchange.cancelOrder (id, symbol);
        console.log ('test failed');
        assert (false);
    } catch (e) {
        if (e instanceof ccxt.OrderNotFound) {
            console.log ('OrderNotFound thrown as expected');
        } else {
            console.log ('OrderNotFound test failed');
            throw e;
        }
    }
};

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/errors/test.OrderNotFound.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 21
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
npm test ts/src/test/base/errors/test.OrderNotFound.ts
```

