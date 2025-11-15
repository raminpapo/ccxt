# Documentation: js/src/test/Exchange/test.fetchLiquidations.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchLiquidations.js`
- **Size**: 826 bytes
- **Lines**: 19
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testSharedMethods from './base/test.sharedMethods.js';
import testLiquidation from './base/test.liquidation.js';
async function testFetchLiquidations(exchange, skippedProperties, code) {
    const method = 'fetchLiquidations';
    if (!exchange.has['fetchLiquidations']) {
        return true;
    }
    const items = await exchange.fetchLiquidations(code);
    assert(Array.isArray(items), exchange.id + ' ' + method + ' ' + code + ' must return an array. ' + exchange.json(items));
    // const now = exchange.milliseconds ();
    for (let i = 0; i < items.length; i++) {
        testLiquidation(exchange, skippedProperties, method, items[i], code);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, code, items);
    return true;
}
export default testFetchLiquidations;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchLiquidations.js`.

**Functions defined**: testFetchLiquidations

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 17
- Comment lines: 1
- Blank lines: 1

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
- `assert` (imported)
- `./base/test.liquidation.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchLiquidations.js
```

