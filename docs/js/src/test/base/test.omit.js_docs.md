# Documentation: js/src/test/base/test.omit.js

## File Metadata

- **Path**: `js/src/test/base/test.omit.js`
- **Size**: 1,667 bytes
- **Lines**: 20
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// AUTO_TRANSPILE_ENABLED
import ccxt from '../../../ccxt.js';
import testSharedMethods from '../Exchange/base/test.sharedMethods.js';
function testOmit() {
    const exchange = new ccxt.Exchange({
        'id': 'sampleexchange',
    });
    testSharedMethods.assertDeepEqual(exchange, undefined, 'testOmit', exchange.omit({}, 'foo'), {});
    testSharedMethods.assertDeepEqual(exchange, undefined, 'testOmit', exchange.omit({ 'foo': 2 }, 'foo'), {});
    testSharedMethods.assertDeepEqual(exchange, undefined, 'testOmit', exchange.omit({ 'foo': 2, 'bar': 3 }, 'foo'), { 'bar': 3 });
    testSharedMethods.assertDeepEqual(exchange, undefined, 'testOmit', exchange.omit({ 'foo': 2, 'bar': 3 }, ['foo']), { 'bar': 3 });
    // todo: below will be added later
    // testSharedMethods.assertDeepEqual (exchange, undefined, 'testOmit',  exchange.omit ({ 'foo': 2, 'bar': 3 }), { 'foo': 2, 'bar': 3 }); // todo: bugs in php, ArgumentCountError: Too few arguments to function ccxt\Exchange::omit(), 1 passed in 2 expected
    // testSharedMethods.assertDeepEqual (exchange, undefined, 'testOmit',  exchange.omit ({ 'foo': 2, 'bar': 3 }, 'foo', 'bar'), {}); // todo: bugs in php
    // testSharedMethods.assertDeepEqual (exchange, undefined, 'testOmit',  exchange.omit ({ 'foo': 2, 'bar': 3 }, [ 'foo' ], 'bar'), {}); // todo: bugs in php
    // testSharedMethods.assertDeepEqual (exchange, undefined, 'testOmit',  exchange.omit ({ '5': 2, 'bar': 3 }, [ 5 ]), { 'bar': 3 }); // todo: bugs in py
    // testSharedMethods.assertDeepEqual (exchange, undefined, 'testOmit',  exchange.omit ({ '5': 2, 'bar': 3 }, 5), { 'bar': 3 }); // todo: bugs in py
}
export default testOmit;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/test.omit.js`.

**Functions defined**: testOmit, ccxt

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 12
- Comment lines: 7
- Blank lines: 1

### Main Components

**Functions** (2):
- `ccxt()`
- `testOmit()`



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
npm test js/src/test/base/test.omit.js
```

