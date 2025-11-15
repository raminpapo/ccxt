# Documentation: js/src/test/Exchange/base/test.borrowRate.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.borrowRate.js`
- **Size**: 1,099 bytes
- **Lines**: 20
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './test.sharedMethods.js';
function testBorrowRate(exchange, skippedProperties, method, entry, requestedCode) {
    const format = {
        'info': {},
        'currency': 'USDT',
        'timestamp': 1638230400000,
        'datetime': '2021-11-30T00:00:00.000Z',
        'rate': exchange.parseNumber('0.0006'),
        'period': 86400000, // Amount of time the interest rate is based on in milliseconds
    };
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format);
    testSharedMethods.assertTimestampAndDatetime(exchange, skippedProperties, method, entry);
    testSharedMethods.assertCurrencyCode(exchange, skippedProperties, method, entry, entry['currency'], requestedCode);
    //
    // assert (borrowRate['period'] === 86400000 || borrowRate['period'] === 3600000) // Milliseconds in an hour or a day
    testSharedMethods.assertGreater(exchange, skippedProperties, method, entry, 'period', '0');
    testSharedMethods.assertGreater(exchange, skippedProperties, method, entry, 'rate', '0');
}
export default testBorrowRate;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.borrowRate.js`.

**Functions defined**: testBorrowRate

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 17
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testBorrowRate()`



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
npm test js/src/test/Exchange/base/test.borrowRate.js
```

