# Documentation: js/src/test/Exchange/test.fetchMarketLeverageTiers.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchMarketLeverageTiers.js`
- **Size**: 602 bytes
- **Lines**: 13
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testLeverageTier from './base/test.leverageTier.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchMarketLeverageTiers(exchange, skippedProperties, symbol) {
    const method = 'fetchMarketLeverageTiers';
    const tiers = await exchange.fetchMarketLeverageTiers(symbol);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, tiers, symbol);
    for (let j = 0; j < tiers.length; j++) {
        testLeverageTier(exchange, skippedProperties, method, tiers[j]);
    }
    return true;
}
export default testFetchMarketLeverageTiers;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchMarketLeverageTiers.js`.

**Functions defined**: testFetchMarketLeverageTiers

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 12
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchMarketLeverageTiers()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.leverageTier.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.leverageTier.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchMarketLeverageTiers.js
```

