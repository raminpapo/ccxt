# Documentation: js/src/test/Exchange/base/test.tradingFee.js

## File Metadata

- **Path**: `js/src/test/Exchange/base/test.tradingFee.js`
- **Size**: 780 bytes
- **Lines**: 17
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './test.sharedMethods.js';
function testTradingFee(exchange, skippedProperties, method, symbol, entry) {
    const format = {
        'info': {},
        'symbol': 'ETH/BTC',
        'maker': exchange.parseNumber('0.002'),
        'taker': exchange.parseNumber('0.003'),
        // todo: most exchanges do not have the below props implemented, so comment out it temporarily
        // 'percentage': false,
        // 'tierBased': false,
    };
    const emptyAllowedFor = ['tierBased', 'percentage', 'symbol'];
    testSharedMethods.assertStructure(exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertSymbol(exchange, skippedProperties, method, entry, 'symbol', symbol);
}
export default testTradingFee;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/base/test.tradingFee.js`.

**Functions defined**: testTradingFee

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 13
- Comment lines: 3
- Blank lines: 1

### Main Components

**Functions** (1):
- `testTradingFee()`



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
npm test js/src/test/Exchange/base/test.tradingFee.js
```

