# Documentation: js/src/test/base/errors/test.OrderNotFound.js

## File Metadata

- **Path**: `js/src/test/base/errors/test.OrderNotFound.js`
- **Size**: 784 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// ----------------------------------------------------------------------------
// @ts-nocheck
import assert from 'assert';
import ccxt from '../../../ccxt.js';
// ----------------------------------------------------------------------------
export default async (exchange, symbol) => {
    if (!exchange.has.createOrder) {
        console.log('createOrder() is not supported');
        return;
    }
    const id = 1;
    try {
        await exchange.cancelOrder(id, symbol);
        console.log('test failed');
        assert(false);
    }
    catch (e) {
        if (e instanceof ccxt.OrderNotFound) {
            console.log('OrderNotFound thrown as expected');
        }
        else {
            console.log('OrderNotFound test failed');
            throw e;
        }
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/errors/test.OrderNotFound.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 23
- Comment lines: 3
- Blank lines: 1

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
npm test js/src/test/base/errors/test.OrderNotFound.js
```

