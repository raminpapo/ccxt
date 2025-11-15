# Documentation: js/src/test/Exchange/test.loadMarkets.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.loadMarkets.js`
- **Size**: 1,052 bytes
- **Lines**: 21
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testMarket from './base/test.market.js';
async function testLoadMarkets(exchange, skippedProperties) {
    const method = 'loadMarkets';
    const markets = await exchange.loadMarkets();
    assert(typeof exchange.markets === 'object', '.markets is not an object');
    assert(Array.isArray(exchange.symbols), '.symbols is not an array');
    const symbolsLength = exchange.symbols.length;
    const marketKeys = Object.keys(exchange.markets);
    const marketKeysLength = marketKeys.length;
    assert(symbolsLength > 0, '.symbols count <= 0 (less than or equal to zero)');
    assert(marketKeysLength > 0, '.markets objects keys length <= 0 (less than or equal to zero)');
    assert(symbolsLength === marketKeysLength, 'number of .symbols is not equal to the number of .markets');
    const marketValues = Object.values(markets);
    for (let i = 0; i < marketValues.length; i++) {
        testMarket(exchange, skippedProperties, method, marketValues[i]);
    }
    return true;
}
export default testLoadMarkets;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.loadMarkets.js`.

**Functions defined**: testLoadMarkets

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 20
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testLoadMarkets()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.market.js` (imported)
- `assert` (imported)
- `./base/test.market.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.loadMarkets.js
```

