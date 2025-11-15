# Documentation: js/src/test/Exchange/base/test.lastPrice.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.lastPrice.js`
- **Size**: 958 bytes
- **Lines**: 19
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './test.sharedMethods.js';
function testLastPrice(exchange, skippedProperties, method, entry, symbol) {
    const format = {
        'info': {},
        'symbol': 'ETH/BTC',
        'timestamp': 1502962946216,
        'datetime': '2017-09-01T00:00:00',
        'price': exchange.parseNumber('1.234'),
        'side': 'buy', // buy or sell
    };
    const emptyAllowedFor = ['timestamp', 'datetime', 'side', 'price']; // binance sometimes provides empty prices for old pairs
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertTimestampAndDatetime(exchange, skippedProperties, method, entry);
    //
    testSharedMethods.assertGreater(exchange, skippedProperties, method, entry, 'price', '0');
    testSharedMethods.assertInArray(exchange, skippedProperties, method, entry, 'side', ['buy', 'sell', undefined]);
}
export default testLastPrice;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.lastPrice.js`.

**Functions defined**: testLastPrice

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 17
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testLastPrice()`



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
npm test js/src/test/Exchange/base/test.lastPrice.js
```

