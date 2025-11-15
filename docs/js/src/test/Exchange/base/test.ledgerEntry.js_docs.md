# Documentation: js/src/test/Exchange/base/test.ledgerEntry.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.ledgerEntry.js`
- **Size**: 1,906 bytes
- **Lines**: 34
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './test.sharedMethods.js';
function testLedgerEntry(exchange, skippedProperties, method, entry, requestedCode, now) {
    const format = {
        'info': {},
        'id': 'x1234',
        'currency': 'BTC',
        'account': 'spot',
        'referenceId': 'foo',
        'referenceAccount': 'bar',
        'status': 'ok',
        'amount': exchange.parseNumber('22'),
        'before': exchange.parseNumber('111'),
        'after': exchange.parseNumber('133'),
        'fee': {},
        'direction': 'in',
        'timestamp': 1638230400000,
        'datetime': '2021-11-30T00:00:00.000Z',
        'type': 'deposit',
    };
    const emptyAllowedFor = ['referenceId', 'referenceAccount', 'id'];
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertTimestampAndDatetime(exchange, skippedProperties, method, entry, now);
    testSharedMethods.assertCurrencyCode(exchange, skippedProperties, method, entry, entry['currency'], requestedCode);
    //
    testSharedMethods.assertInArray(exchange, skippedProperties, method, entry, 'direction', ['in', 'out']);
    testSharedMethods.assertInArray(exchange, skippedProperties, method, entry, 'type', ['trade', 'transaction', 'margin', 'cashback', 'referral', 'transfer', 'fee']);
    // testSharedMethods.assertInArray (exchange, skippedProperties, method, entry, 'account', ['spot', 'swap', .. ]); // todo
    testSharedMethods.assertGreaterOrEqual(exchange, skippedProperties, method, entry, 'amount', '0');
    testSharedMethods.assertGreaterOrEqual(exchange, skippedProperties, method, entry, 'before', '0');
    testSharedMethods.assertGreaterOrEqual(exchange, skippedProperties, method, entry, 'after', '0');
    // testSharedMethods.assertFeeStructure (exchange, skippedProperties, method, entry, 'fee');
}
export default testLedgerEntry;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.ledgerEntry.js`.

**Functions defined**: testLedgerEntry

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 30
- Comment lines: 3
- Blank lines: 1

### Main Components

**Functions** (1):
- `testLedgerEntry()`



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
npm test js/src/test/Exchange/base/test.ledgerEntry.js
```

