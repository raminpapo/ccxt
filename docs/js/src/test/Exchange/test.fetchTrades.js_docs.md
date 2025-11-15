# Documentation: js/src/test/Exchange/test.fetchTrades.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchTrades.js`
- **Size**: 845 bytes
- **Lines**: 18
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './base/test.sharedMethods.js';
import testTrade from './base/test.trade.js';
async function testFetchTrades(exchange, skippedProperties, symbol) {
    const method = 'fetchTrades';
    const trades = await exchange.fetchTrades(symbol);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, trades);
    const now = exchange.milliseconds();
    for (let i = 0; i < trades.length; i++) {
        testTrade(exchange, skippedProperties, method, trades[i], symbol, now);
        testSharedMethods.assertInArray(exchange, skippedProperties, method, trades[i], 'takerOrMaker', ['taker', undefined]);
    }
    if (!('timestampSort' in skippedProperties)) {
        testSharedMethods.assertTimestampOrder(exchange, method, symbol, trades);
    }
    return true;
}
export default testFetchTrades;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchTrades.js`.

**Functions defined**: testFetchTrades

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 17
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchTrades()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.trade.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `./base/test.trade.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchTrades.js
```

