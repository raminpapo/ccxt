# Documentation: js/src/test/Exchange/test.fetchMarkets.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchMarkets.js`
- **Size**: 1,419 bytes
- **Lines**: 33
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testMarket from './base/test.market.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchMarkets(exchange, skippedProperties) {
    const method = 'fetchMarkets';
    const markets = await exchange.fetchMarkets();
    assert(typeof markets === 'object', exchange.id + ' ' + method + ' must return an object. ' + exchange.json(markets));
    const marketValues = Object.values(markets);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, marketValues);
    for (let i = 0; i < marketValues.length; i++) {
        testMarket(exchange, skippedProperties, method, marketValues[i]);
    }
    detectMarketConflicts(exchange, markets);
    return true;
}
function detectMarketConflicts(exchange, marketValues) {
    // detect if there are markets with different ids for the same symbol
    const ids = {};
    for (let i = 0; i < marketValues.length; i++) {
        const market = marketValues[i];
        const symbol = market['symbol'];
        if (!(symbol in ids)) {
            ids[symbol] = market['id'];
        }
        else {
            const isDifferent = ids[symbol] !== market['id'];
            assert(!isDifferent, exchange.id + ' fetchMarkets() has different ids for the same symbol: ' + symbol + ' ' + ids[symbol] + ' ' + market['id']);
        }
    }
    return true;
}
export default testFetchMarkets;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchMarkets.js`.

**Functions defined**: testFetchMarkets, detectMarketConflicts

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 31
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (2):
- `detectMarketConflicts()`
- `testFetchMarkets()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.market.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `./base/test.market.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchMarkets.js
```

