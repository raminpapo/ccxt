# Documentation: js/src/test/base/test.filterBy.js

## File Metadata

- **Path**: `js/src/test/base/test.filterBy.js`
- **Size**: 839 bytes
- **Lines**: 28
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// AUTO_TRANSPILE_ENABLED
import ccxt from '../../../ccxt.js';
import testSharedMethods from '../Exchange/base/test.sharedMethods.js';
function testFilterBy() {
    const exchange = new ccxt.Exchange({
        'id': 'sampleexchange',
    });
    const sampleArray = [
        { 'foo': 'a' },
        { 'foo': undefined },
        { 'foo': 'b' },
        // { }, todo : bugs in py
        { 'foo': 'a', 'bar': 'b' },
        { 'foo': 'c' },
        { 'foo': 'd' },
        { 'foo': 'b' },
        { 'foo': 'c' },
        { 'foo': 'c' },
    ];
    const currentValue = exchange.filterBy(sampleArray, 'foo', 'a');
    const storedValue = [
        { 'foo': 'a' },
        { 'foo': 'a', 'bar': 'b' },
    ];
    testSharedMethods.assertDeepEqual(exchange, undefined, 'testFilterBy', currentValue, storedValue);
}
export default testFilterBy;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/test.filterBy.js`.

**Functions defined**: testFilterBy

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 25
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFilterBy()`



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
npm test js/src/test/base/test.filterBy.js
```

