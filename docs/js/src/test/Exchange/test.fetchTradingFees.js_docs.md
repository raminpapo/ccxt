# Documentation: js/src/test/Exchange/test.fetchTradingFees.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchTradingFees.js`
- **Size**: 631 bytes
- **Lines**: 15
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testTradingFee from './base/test.tradingFee.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchTradingFees(exchange, skippedProperties) {
    const method = 'fetchTradingFees';
    const fees = await exchange.fetchTradingFees();
    const symbols = Object.keys(fees);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, symbols);
    for (let i = 0; i < symbols.length; i++) {
        const symbol = symbols[i];
        testTradingFee(exchange, skippedProperties, method, symbol, fees[symbol]);
    }
    return true;
}
export default testFetchTradingFees;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchTradingFees.js`.

**Functions defined**: testFetchTradingFees

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 14
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchTradingFees()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.tradingFee.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.tradingFee.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchTradingFees.js
```

