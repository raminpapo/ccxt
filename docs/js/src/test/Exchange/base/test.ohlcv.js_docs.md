# Documentation: js/src/test/Exchange/base/test.ohlcv.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.ohlcv.js`
- **Size**: 1,666 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testSharedMethods from './test.sharedMethods.js';
function testOHLCV(exchange, skippedProperties, method, entry, symbol, now) {
    const format = [
        1638230400000,
        exchange.parseNumber('0.123'),
        exchange.parseNumber('0.125'),
        exchange.parseNumber('0.121'),
        exchange.parseNumber('0.122'),
        exchange.parseNumber('123.456'),
    ];
    const emptyNotAllowedFor = [0, 1, 2, 3, 4, 5];
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format, emptyNotAllowedFor);
    testSharedMethods.assertTimestampAndDatetime(exchange, skippedProperties, method, entry, now, 0);
    const logText = testSharedMethods.logTemplate(exchange, method, entry);
    //
    assert(entry.length >= 6, 'ohlcv array length should be >= 6;' + logText);
    if (!('roundTimestamp' in skippedProperties)) {
        testSharedMethods.assertRoundMinuteTimestamp(exchange, skippedProperties, method, entry, 0);
    }
    const high = exchange.safeString(entry, 2);
    const low = exchange.safeString(entry, 3);
    testSharedMethods.assertLessOrEqual(exchange, skippedProperties, method, entry, '1', high);
    testSharedMethods.assertGreaterOrEqual(exchange, skippedProperties, method, entry, '1', low);
    testSharedMethods.assertLessOrEqual(exchange, skippedProperties, method, entry, '4', high);
    testSharedMethods.assertGreaterOrEqual(exchange, skippedProperties, method, entry, '4', low);
    assert((symbol === undefined) || (typeof symbol === 'string'), 'symbol ' + symbol + ' is incorrect' + logText); // todo: check with standard symbol check
}
export default testOHLCV;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.ohlcv.js`.

**Functions defined**: testOHLCV

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 28
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testOHLCV()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./test.sharedMethods.js` (imported)
- `assert` (imported)
- `./test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/base/test.ohlcv.js
```

