# Documentation: js/src/test/base/test.extend.js

## File Metadata

- **Path**: `js/src/test/base/test.extend.js`
- **Size**: 1,814 bytes
- **Lines**: 65
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// AUTO_TRANSPILE_ENABLED
import assert from 'assert';
import ccxt from '../../../ccxt.js';
function testExtend() {
    const exchange = new ccxt.Exchange({
        'id': 'regirock',
    });
    const obj1 = {
        "a": 1,
        "b": [1, 2],
        "c": [{ "test1": 1, "test2": 1 }],
        "d": undefined,
        "e": "not_undefined",
        "sub": {
            "a": 1,
            "b": [1, 2],
            "c": [{ "test1": 1, "test2": 2 }],
            "d": undefined,
            "e": "not_undefined",
            "other1": "x",
        },
        "other1": "x",
    };
    const obj2 = {
        "a": 2,
        "b": [3, 4],
        "c": [{ "test1": 2, "test3": 3 }],
        "d": "not_undefined",
        "e": undefined,
        "sub": {
            "a": 2,
            "b": [3, 4],
            "c": [{ "test1": 2, "test3": 3 }],
            "d": "not_undefined",
            "e": undefined,
            "other2": "y",
        },
        "other2": "y",
    };
    // extend
    const extended = exchange.extend(obj1, obj2);
    tbfeCheckExtended(extended, true);
    // deepExtend
    // const deepExtended = exchange.deepExtend (obj1, obj2);
    // tbfeCheckExtended (extended, true);
    // todo !
    // tbfeCheckExtended (deepExtended["sub"], false);
}
function tbfeCheckExtended(extended, hasSub) {
    assert(extended["a"] === 2);
    assert(extended["b"][0] === 3);
    assert(extended["b"][1] === 4);
    assert(extended["c"][0]["test1"] === 2);
    assert(!("test2" in extended["c"][0]));
    assert(extended["c"][0]["test3"] === 3);
    assert(extended["d"] === "not_undefined");
    assert(extended["e"] === undefined);
    assert(extended["other1"] === "x");
    assert(extended["other2"] === "y");
    if (hasSub) {
        assert("sub" in extended);
    }
}
export default testExtend;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/test.extend.js`.

**Functions defined**: tbfeCheckExtended, testExtend

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 57
- Comment lines: 7
- Blank lines: 1

### Main Components

**Functions** (2):
- `tbfeCheckExtended()`
- `testExtend()`



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
npm test js/src/test/base/test.extend.js
```

