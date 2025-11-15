# Documentation: js/src/test/base/test.setMarketsFromExchange.js

## File Metadata

- **Path**: `js/src/test/base/test.setMarketsFromExchange.js`
- **Size**: 2,207 bytes
- **Lines**: 48
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testSharedMethods from '../Exchange/base/test.sharedMethods.js';
import ccxt from "../../../ccxt.js";
async function testSetMarketsFromExchange(exchange) {
    const method = 'testSetMarketsFromExchange';
    console.log(exchange.id, method);
    // Test 1: Basic market sharing
    const exchange1 = new ccxt.binance({});
    const exchange2 = new ccxt.binance({});
    // Load markets in first exchange
    const markets1 = await exchange1.loadMarkets();
    assert(Object.keys(markets1).length > 0, 'Markets should be loaded in exchange1');
    // Test error case: exchanges are different
    const differentExchange = new ccxt.coinbase({});
    try {
        differentExchange.setMarketsFromExchange(exchange1);
        assert(false, 'Should have thrown an error when using different exchange');
    }
    catch (error) {
        assert(true);
    }
    // Test error case: sharing from exchange without markets
    const emptyExchange = new ccxt.binance({});
    try {
        exchange2.setMarketsFromExchange(emptyExchange); // exchange2 has no markets yet
        assert(false, 'Should have thrown error when sharing from exchange without markets');
    }
    catch (error) {
        assert(true);
    }
    // Test the new setMarketsFromExchange method
    exchange2.setMarketsFromExchange(exchange1);
    // Verify shared markets work
    assert(testSharedMethods.deepEqual(exchange1.symbols, exchange2.symbols), 'Symbols should be available after market sharing');
    assert(testSharedMethods.deepEqual(exchange1.currencies, exchange2.currencies), 'currencies dont match');
    assert(testSharedMethods.deepEqual(exchange1.codes, exchange2.codes), 'codes dont match');
    // TODO: add rest of assertions
    // Test 2: loadMarkets on shared markets should not make API call and be very fast
    const startTime = Date.now();
    await exchange2.loadMarkets();
    const endTime = Date.now();
    // Should be very fast since no API call is made
    const timeTaken = endTime - startTime;
    assert(timeTaken < 10, 'loadMarkets on shared markets should be fast');
}
testSetMarketsFromExchange(new ccxt.binance({}));
export default testSetMarketsFromExchange;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/test.setMarketsFromExchange.js`.

**Functions defined**: testSetMarketsFromExchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 38
- Comment lines: 9
- Blank lines: 1

### Main Components

**Functions** (1):
- `testSetMarketsFromExchange()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../Exchange/base/test.sharedMethods.js` (imported)
- `../../../ccxt.js` (imported)
- `assert` (imported)
- `../Exchange/base/test.sharedMethods.js` (referenced)
- `../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/base/test.setMarketsFromExchange.js
```

