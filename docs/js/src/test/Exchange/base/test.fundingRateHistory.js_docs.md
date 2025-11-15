# Documentation: js/src/test/Exchange/base/test.fundingRateHistory.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.fundingRateHistory.js`
- **Size**: 893 bytes
- **Lines**: 17
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './test.sharedMethods.js';
function testFundingRateHistory(exchange, skippedProperties, method, entry, symbol) {
    const format = {
        'info': {},
        'symbol': 'BTC/USDT:USDT',
        'timestamp': 1638230400000,
        'datetime': '2021-11-30T00:00:00.000Z',
        'fundingRate': exchange.parseNumber('0.0006'),
    };
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format);
    testSharedMethods.assertSymbol(exchange, skippedProperties, method, entry, 'symbol', symbol);
    testSharedMethods.assertTimestampAndDatetime(exchange, skippedProperties, method, entry);
    testSharedMethods.assertGreater(exchange, skippedProperties, method, entry, 'fundingRate', '-100');
    testSharedMethods.assertLess(exchange, skippedProperties, method, entry, 'fundingRate', '100');
}
export default testFundingRateHistory;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.fundingRateHistory.js`.

**Functions defined**: testFundingRateHistory

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 16
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFundingRateHistory()`



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
npm test js/src/test/Exchange/base/test.fundingRateHistory.js
```

