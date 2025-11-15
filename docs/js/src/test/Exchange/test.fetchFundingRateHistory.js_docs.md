# Documentation: js/src/test/Exchange/test.fetchFundingRateHistory.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchFundingRateHistory.js`
- **Size**: 771 bytes
- **Lines**: 14
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testFundingRateHistory from './base/test.fundingRateHistory.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchFundingRateHistory(exchange, skippedProperties, symbol) {
    const method = 'fetchFundingRateHistory';
    const fundingRatesHistory = await exchange.fetchFundingRateHistory(symbol);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, fundingRatesHistory, symbol);
    for (let i = 0; i < fundingRatesHistory.length; i++) {
        testFundingRateHistory(exchange, skippedProperties, method, fundingRatesHistory[i], symbol);
    }
    testSharedMethods.assertTimestampOrder(exchange, method, symbol, fundingRatesHistory);
    return true;
}
export default testFetchFundingRateHistory;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchFundingRateHistory.js`.

**Functions defined**: testFetchFundingRateHistory

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 13
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchFundingRateHistory()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.fundingRateHistory.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.fundingRateHistory.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchFundingRateHistory.js
```

