# Documentation: js/src/test/Exchange/base/test.balance.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.balance.js`
- **Size**: 2,581 bytes
- **Lines**: 46
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import Precise from '../../../base/Precise.js';
import testSharedMethods from './test.sharedMethods.js';
function testBalance(exchange, skippedProperties, method, entry) {
    const format = {
        'free': {},
        'used': {},
        'total': {},
        'info': {},
    };
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format);
    const logText = testSharedMethods.logTemplate(exchange, method, entry);
    //
    const codesTotal = Object.keys(entry['total']);
    const codesFree = Object.keys(entry['free']);
    const codesUsed = Object.keys(entry['used']);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, codesTotal, 'total');
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, codesFree, 'free');
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, codesUsed, 'used');
    let allCodes = exchange.arrayConcat(codesTotal, codesFree);
    allCodes = exchange.arrayConcat(allCodes, codesUsed);
    const codesLength = codesTotal.length;
    const freeLength = codesFree.length;
    const usedLength = codesUsed.length;
    assert((codesLength === freeLength) || (codesLength === usedLength), 'free and total and used codes have different lengths' + logText);
    for (let i = 0; i < allCodes.length; i++) {
        const code = allCodes[i];
        // testSharedMethods.assertCurrencyCode (exchange, skippedProperties, method, entry, code);
        assert(code in entry['total'], 'code ' + code + ' not in total' + logText);
        assert(code in entry['free'], 'code ' + code + ' not in free' + logText);
        assert(code in entry['used'], 'code ' + code + ' not in used' + logText);
        const total = exchange.safeString(entry['total'], code);
        const free = exchange.safeString(entry['free'], code);
        const used = exchange.safeString(entry['used'], code);
        assert(total !== undefined, 'total is undefined' + logText);
        assert(free !== undefined, 'free is undefined' + logText);
        assert(used !== undefined, 'used is undefined' + logText);
        assert(Precise.stringGe(total, '0'), 'total is not positive' + logText);
        assert(Precise.stringGe(free, '0'), 'free is not positive' + logText);
        assert(Precise.stringGe(used, '0'), 'used is not positive' + logText);
        const sumFreeUsed = Precise.stringAdd(free, used);
        assert(Precise.stringEq(total, sumFreeUsed), 'free and used do not sum to total' + logText);
    }
}
export default testBalance;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.balance.js`.

**Functions defined**: testBalance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 43
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testBalance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./test.sharedMethods.js` (imported)
- `../../../base/Precise.js` (imported)
- `assert` (imported)
- `./test.sharedMethods.js` (referenced)
- `../../../base/Precise.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/base/test.balance.js
```

