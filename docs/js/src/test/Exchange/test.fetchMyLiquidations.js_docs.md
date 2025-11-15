# Documentation: js/src/test/Exchange/test.fetchMyLiquidations.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchMyLiquidations.js`
- **Size**: 836 bytes
- **Lines**: 19
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testSharedMethods from './base/test.sharedMethods.js';
import testLiquidation from './base/test.liquidation.js';
async function testFetchMyLiquidations(exchange, skippedProperties, code) {
    const method = 'fetchMyLiquidations';
    if (!exchange.has['fetchMyLiquidations']) {
        return true;
    }
    const items = await exchange.fetchMyLiquidations(code);
    assert(Array.isArray(items), exchange.id + ' ' + method + ' ' + code + ' must return an array. ' + exchange.json(items));
    // const now = exchange.milliseconds ();
    for (let i = 0; i < items.length; i++) {
        testLiquidation(exchange, skippedProperties, method, items[i], code);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, code, items);
    return true;
}
export default testFetchMyLiquidations;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchMyLiquidations.js`.

**Functions defined**: testFetchMyLiquidations

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 17
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchMyLiquidations()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.liquidation.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `./base/test.liquidation.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchMyLiquidations.js
```

