# Documentation: js/src/test/base/language_specific/test.aggregate.js

## File Metadata

- **Path**: `js/src/test/base/language_specific/test.aggregate.js`
- **Size**: 900 bytes
- **Lines**: 33
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// @ts-nocheck
// todo: per https://github.com/ttodua/ccxt/blob/428f5b50da50b7401caa5ac452538fb0f6641af4/ts/src/test/base/test.aggregate.ts
import { strictEqual, deepEqual } from 'assert';
import { functions } from '../../../../ccxt.js';
const { index, aggregate, unCamelCase } = functions;
const equal = strictEqual;
function testAggregate() {
    const bids = [
        [789.1, 123.0],
        [789.100, 123.0],
        [123.0, 456.0],
        [789.0, 123.0],
        [789.10, 123.0],
    ];
    const asks = [
        [123.0, 456.0],
        [789.0, 123.0],
        [789.10, 123.0],
    ];
    deepEqual(aggregate(bids.sort()), [
        [123.0, 456.0],
        [789.0, 123.0],
        [789.1, 369.0],
    ]);
    deepEqual(aggregate(asks.sort()), [
        [123.0, 456.0],
        [789.0, 123.0],
        [789.10, 123.0],
    ]);
    deepEqual(aggregate([]), []);
}
export default testAggregate;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/language_specific/test.aggregate.js`.

**Functions defined**: testAggregate

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 30
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testAggregate()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/base/language_specific/test.aggregate.js
```

