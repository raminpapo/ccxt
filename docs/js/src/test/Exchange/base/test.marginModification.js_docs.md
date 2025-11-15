# Documentation: js/src/test/Exchange/base/test.marginModification.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.marginModification.js`
- **Size**: 1,265 bytes
- **Lines**: 23
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './test.sharedMethods.js';
function testMarginModification(exchange, skippedProperties, method, entry) {
    const format = {
        'info': {},
        'type': 'add',
        'amount': exchange.parseNumber('0.1'),
        'total': exchange.parseNumber('0.29934828'),
        'code': 'USDT',
        'symbol': 'ADA/USDT:USDT',
        'status': 'ok',
    };
    const emptyAllowedFor = ['status', 'symbol', 'code', 'total', 'amount'];
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertCurrencyCode(exchange, skippedProperties, method, entry, entry['code']);
    //
    testSharedMethods.assertGreaterOrEqual(exchange, skippedProperties, method, entry, 'amount', '0');
    testSharedMethods.assertGreaterOrEqual(exchange, skippedProperties, method, entry, 'total', '0');
    testSharedMethods.assertInArray(exchange, skippedProperties, method, entry, 'type', ['add', 'reduce', 'set']);
    testSharedMethods.assertInArray(exchange, skippedProperties, method, entry, 'status', ['ok', 'pending', 'canceled', 'failed']);
    testSharedMethods.assertSymbol(exchange, skippedProperties, method, entry, 'symbol');
}
export default testMarginModification;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.marginModification.js`.

**Functions defined**: testMarginModification

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 21
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testMarginModification()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./test.sharedMethods.js` (imported)
- `./test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/base/test.marginModification.js
```

