# Documentation: js/src/pro/test/Exchange/test.watchOrderBook.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchOrderBook.js`
- **Size**: 2,656 bytes
- **Lines**: 52
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testOrderBook from '../../../test/Exchange/base/test.orderBook.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchOrderBook(exchange, skippedProperties, symbol) {
    const method = 'watchOrderBook';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchOrderBook(symbol);
        }
        catch (e) {
            if (!testSharedMethods.isTemporaryFailure(e)) {
                throw e;
            }
            now = exchange.milliseconds();
            // continue;
            success = false;
        }
        if (success === true) {
            // [ response, skippedProperties ] = fixPhpObjectArray (exchange, response, skippedProperties);
            assert(typeof response === 'object', exchange.id + ' ' + method + ' ' + symbol + ' must return an object. ' + exchange.json(response));
            now = exchange.milliseconds();
            testOrderBook(exchange, skippedProperties, method, response, symbol);
        }
    }
    return true;
}
// function fixPhpObjectArray (exchange, response, skippedProperties) {
//     // temp fix for php 'Pro\OrderBook' object, to turn it into array
//     const existingJqMode = exchange.getProperty (exchange, 'quoteJsonNumbers');
//     exchange.setExchangeProperty ('quoteJsonNumbers', false);
//     const result = exchange.parseJson (exchange.json (response));
//     exchange.setExchangeProperty ('quoteJsonNumbers', existingJqMode);
//     // temporary fix, because after json.strinfigy->parse, 'undefined' members are removed
//     skippedProperties['timestamp'] = true;
//     skippedProperties['datetime'] = true;
//     skippedProperties['nonce'] = true;
//     // ### temporarily fix some bugs for PHP (before they are fixed in library) ###
//     // 1) entries are being unordered in some cases, so before that separate issue is fixed, temporarily fix it here. for example, some entries are weird, like [[price, amount], [price, amount], ["1", amount]]]
//     result['asks'] = exchange.sortBy(result['asks'], 0, false);
//     result['bids'] = exchange.sortBy(result['bids'], 0, true);
//     // 2)  limit to first 100 to avoid PHP memory exhaustion (another bug)
//     result['asks'] = exchange.filterByLimit(result['asks'], 100);
//     result['bids'] = exchange.filterByLimit(result['bids'], 100);
//     // #################################
//     return [ result , skippedProperties ];
// }
export default testWatchOrderBook;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchOrderBook.js`.

**Functions defined**: fixPhpObjectArray, testWatchOrderBook

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 29
- Comment lines: 22
- Blank lines: 1

### Main Components

**Functions** (2):
- `fixPhpObjectArray()`
- `testWatchOrderBook()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.orderBook.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.orderBook.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchOrderBook.js
```

