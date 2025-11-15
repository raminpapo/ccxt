# Documentation: ts/src/test/base/language_specific/test.type.ts

## File Metadata

- **Path**: `ts/src/test/base/language_specific/test.type.ts`
- **Size**: 2,149 bytes
- **Lines**: 63
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/*  ------------------------------------------------------------------------ */
//@ts-nocheck
/* eslint-disable */
import { functions } from '../../../../ccxt.js'
import { equal, deepEqual } from 'assert'

const {
    safeFloat,
    safeInteger,
    safeValue
} = functions;
/*  ------------------------------------------------------------------------ */

function testSafeFloatSafeInteger() {

    const $default = {}

    const fns = { safeFloat, safeInteger }

    for (const fn of ['safeFloat', 'safeInteger']) {

        equal (fns[fn] ({ 'x': false }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': true }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': [] }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': [0] }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': [1] }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': {} }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': Number.NaN }, 'x'), undefined)
        equal (fns[fn] ({ 'x': Number.POSITIVE_INFINITY }, 'x'), undefined)
        equal (fns[fn] ({ 'x': null }, 'x', undefined), undefined)
        equal (fns[fn] ({ 'x': null }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': '1.0' }, 'x'), 1.0)
        equal (fns[fn] ({ 'x': '-1.0' }, 'x'), -1.0)
        equal (fns[fn] ({ 'x': 1.0 }, 'x'), 1.0)
        equal (fns[fn] ({ 'x': 0 }, 'x'), 0)
        equal (fns[fn] ({ 'x': undefined }, 'x', $default), $default)
        equal (fns[fn] ({ 'x': "" }, 'x'), undefined)
        equal (fns[fn] ({ 'x': "" }, 'x', 0), 0)
        equal (fns[fn] ({}, 'x'), undefined)
        equal (fns[fn] ({}, 'x', 0), 0)
    }

    equal (safeFloat   ({ 'x': 1.59999999 }, 'x'), 1.59999999)
    equal (safeInteger ({ 'x': 1.59999999 }, 'x'), 1)
}

function testSafeValue() {

    equal (safeValue ({}, 'foo'), undefined)
    equal (safeValue ({}, 'foo', 'bar'), 'bar')
    equal (safeValue ({ 'foo': 'bar' }, 'foo'), 'bar')
    equal (safeValue ({ 'foo': '' }, 'foo'), undefined)
    equal (safeValue ({ 'foo': 0 }, 'foo'), 0)
}

function testTypeAll () {
    testSafeFloatSafeInteger ()
    testSafeValue ()
}

export default testTypeAll;


```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/language_specific/test.type.ts`.

**Functions defined**: testSafeFloatSafeInteger, testSafeValue, testTypeAll

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 49
- Comment lines: 4
- Blank lines: 10

### Main Components

**Functions** (3):
- `testSafeFloatSafeInteger()`
- `testSafeValue()`
- `testTypeAll()`



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
npm test ts/src/test/base/language_specific/test.type.ts
```

