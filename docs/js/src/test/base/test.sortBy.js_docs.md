# Documentation: js/src/test/base/test.sortBy.js

## File Metadata

- **Path**: `js/src/test/base/test.sortBy.js`
- **Size**: 1,069 bytes
- **Lines**: 32
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// AUTO_TRANSPILE_ENABLED
import ccxt from '../../../ccxt.js';
import testSharedMethods from '../Exchange/base/test.sharedMethods.js';
function testSortBy() {
    // todo: other argument checks
    const exchange = new ccxt.Exchange({
        'id': 'sampleexchange',
    });
    const arr = [{ 'x': 5 }, { 'x': 2 }, { 'x': 4 }, { 'x': 0 }, { 'x': 1 }, { 'x': 3 }];
    const newArray = exchange.sortBy(arr, 'x');
    testSharedMethods.assertDeepEqual(exchange, undefined, 'sortBy', newArray, [
        { 'x': 0 },
        { 'x': 1 },
        { 'x': 2 },
        { 'x': 3 },
        { 'x': 4 },
        { 'x': 5 },
    ]);
    const newArrayDescending = exchange.sortBy(arr, 'x', true);
    testSharedMethods.assertDeepEqual(exchange, undefined, 'sortBy', newArrayDescending, [
        { 'x': 5 },
        { 'x': 4 },
        { 'x': 3 },
        { 'x': 2 },
        { 'x': 1 },
        { 'x': 0 },
    ]);
    const emptyArray = exchange.sortBy([], 'x');
    testSharedMethods.assertDeepEqual(exchange, undefined, 'sortBy', emptyArray, []);
}
export default testSortBy;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/test.sortBy.js`.

**Functions defined**: testSortBy

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 29
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testSortBy()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../ccxt.js` (imported)
- `../Exchange/base/test.sharedMethods.js` (imported)
- `../../../ccxt.js` (referenced)
- `../Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/base/test.sortBy.js
```

