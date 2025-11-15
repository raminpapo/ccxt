# Documentation: js/src/test/Exchange/test.fetchLeverageTiers.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchLeverageTiers.js`
- **Size**: 1,122 bytes
- **Lines**: 25
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testLeverageTier from './base/test.leverageTier.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchLeverageTiers(exchange, skippedProperties, symbol) {
    const method = 'fetchLeverageTiers';
    const tiers = await exchange.fetchLeverageTiers(['symbol']);
    // const format = {
    //     'RAY/USDT': [
    //       {},
    //     ],
    // };
    assert(typeof tiers === 'object', exchange.id + ' ' + method + ' ' + symbol + ' must return an object. ' + exchange.json(tiers));
    const tierKeys = Object.keys(tiers);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, tierKeys, symbol);
    for (let i = 0; i < tierKeys.length; i++) {
        const tiersForSymbol = tiers[tierKeys[i]];
        testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, tiersForSymbol, symbol);
        for (let j = 0; j < tiersForSymbol.length; j++) {
            testLeverageTier(exchange, skippedProperties, method, tiersForSymbol[j]);
        }
    }
    return true;
}
export default testFetchLeverageTiers;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchLeverageTiers.js`.

**Functions defined**: testFetchLeverageTiers

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 19
- Comment lines: 5
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchLeverageTiers()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.leverageTier.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `./base/test.leverageTier.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchLeverageTiers.js
```

