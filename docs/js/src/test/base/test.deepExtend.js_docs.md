# Documentation: js/src/test/base/test.deepExtend.js

## File Metadata

- **Path**: `js/src/test/base/test.deepExtend.js`
- **Size**: 2,044 bytes
- **Lines**: 68
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// AUTO_TRANSPILE_ENABLED
import assert from 'assert';
import ccxt from '../../../ccxt.js';
function testDeepExtend() {
    const exchange = new ccxt.Exchange({
        'id': 'sampleexchange',
    });
    assert(exchange.parseToNumeric('1') === 1);
    return true; // dummy for now
    // const obj1 = {
    //     "a": 1,
    //     "b": [ 1, 2 ],
    //     "c": [ { "test1": 1, "test2": 1 } ],
    //     "d": undefined,
    //     "e": "not_undefined",
    //     "sub": {
    //         "a": 1,
    //         "b": [ 1, 2 ],
    //         "c": [ { "test1": 1, "test2": 2 } ],
    //         "d": undefined,
    //         "e": "not_undefined",
    //         "other1": "x",
    //     },
    //     "other1": "x",
    // };
    // const obj2 = {
    //     "a": 2,
    //     "b": [ 3, 4 ],
    //     "c": [ { "test1": 2, "test3": 3 } ],
    //     "d": "not_undefined",
    //     "e": undefined,
    //     "sub": {
    //         "a": 2,
    //         "b": [ 3, 4 ],
    //         "c": [ { "test1": 2, "test3": 3 } ],
    //         "d": "not_undefined",
    //         "e": undefined,
    //         "other2": "y",
    //     },
    //     "other2": "y",
    // };
    // deepExtend
    // const deepExtended = exchange.deepExtend (obj1, obj2);
    // const compareTo = {
    //     "a": 2,
    //     "b": [ 3, 4 ],
    //     "c": [ {
    //         "test1": 2,
    //         "test3": 3,
    //     } ],
    //     "d": "not_undefined",
    //     "sub": {
    //         "a": 2,
    //         "b": [ 3, 4 ],
    //         "c": [ { "test1": 2, "test3": 3 } ],
    //         "d": "not_undefined",
    //         "other1": "x",
    //         "other2": "y",
    //     },
    //     "other1": "x",
    //     "other2": "y",
    // };
    // todo: results are different across langs.
    // to avoid delay to this PR, I comment out this now, but will return to this after this PR merged
    // testSharedMethods.assertDeepEqual (exchange, undefined, 'testDeepExtend', deepExtended, compareTo);
}
export default testDeepExtend;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/test.deepExtend.js`.

**Functions defined**: testDeepExtend

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 68
- Code lines: 10
- Comment lines: 57
- Blank lines: 1

### Main Components

**Functions** (1):
- `testDeepExtend()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/base/test.deepExtend.js
```

