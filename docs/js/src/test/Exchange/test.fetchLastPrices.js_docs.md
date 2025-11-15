# Documentation: js/src/test/Exchange/test.fetchLastPrices.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchLastPrices.js`
- **Size**: 1,329 bytes
- **Lines**: 29
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testLastPrice from './base/test.lastPrice.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchLastPrices(exchange, skippedProperties, symbol) {
    const method = 'fetchLastprices';
    // log ('fetching all tickers at once...')
    let response = undefined;
    let checkedSymbol = undefined;
    try {
        response = await exchange.fetchLastPrices();
    }
    catch (e) {
        response = await exchange.fetchLastPrices([symbol]);
        checkedSymbol = symbol;
    }
    assert(typeof response === 'object', exchange.id + ' ' + method + ' ' + checkedSymbol + ' must return an object. ' + exchange.json(response));
    const values = Object.values(response);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, values, checkedSymbol);
    let atLeastOnePassed = false;
    for (let i = 0; i < values.length; i++) {
        // todo: symbol check here
        testLastPrice(exchange, skippedProperties, method, values[i], checkedSymbol);
        atLeastOnePassed = atLeastOnePassed || (exchange.safeNumber(values[i], 'price') > 0);
    }
    assert(atLeastOnePassed, exchange.id + ' ' + method + ' ' + checkedSymbol + ' at least one symbol should pass the test');
    return true;
}
export default testFetchLastPrices;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchLastPrices.js`.

**Functions defined**: testFetchLastPrices

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 26
- Comment lines: 2
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchLastPrices()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `./base/test.lastPrice.js` (imported)
- `assert` (imported)
- `./base/test.lastPrice.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchLastPrices.js
```

