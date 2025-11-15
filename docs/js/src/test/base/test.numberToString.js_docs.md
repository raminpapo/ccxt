# Documentation: js/src/test/base/test.numberToString.js

## File Metadata

- **Path**: `js/src/test/base/test.numberToString.js`
- **Size**: 1,442 bytes
- **Lines**: 28
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// AUTO_TRANSPILE_ENABLED
import assert from 'assert';
import ccxt from '../../../ccxt.js';
function testNumberToString() {
    const exchange = new ccxt.Exchange({
        'id': 'regirock',
    });
    // ----------------------------------------------------------------------------
    // numberToString
    assert(exchange.numberToString(-7.8e-7) === '-0.00000078');
    assert(exchange.numberToString(7.8e-7) === '0.00000078');
    assert(exchange.numberToString(-17.805e-7) === '-0.0000017805');
    assert(exchange.numberToString(17.805e-7) === '0.0000017805');
    assert(exchange.numberToString(-7.0005e27) === '-7000500000000000000000000000');
    assert(exchange.numberToString(7.0005e27) === '7000500000000000000000000000');
    assert(exchange.numberToString(-7.9e27) === '-7900000000000000000000000000');
    assert(exchange.numberToString(7e27) === '7000000000000000000000000000');
    assert(exchange.numberToString(7.9e27) === '7900000000000000000000000000');
    assert(exchange.numberToString(-12.345) === '-12.345');
    assert(exchange.numberToString(12.345) === '12.345');
    assert(exchange.numberToString(0) === '0');
    assert(exchange.numberToString(7.35946e21) === '7359460000000000000000');
    assert(exchange.numberToString(0.00000001) === '0.00000001');
    assert(exchange.numberToString(1e-7) === '0.0000001');
    assert(exchange.numberToString(-1e-7) === '-0.0000001');
}
export default testNumberToString;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/test.numberToString.js`.

**Functions defined**: testNumberToString

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 24
- Comment lines: 3
- Blank lines: 1

### Main Components

**Functions** (1):
- `testNumberToString()`



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
npm test js/src/test/base/test.numberToString.js
```

