# Documentation: js/src/pro/test/Exchange/test.watchLiquidations.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchLiquidations.js`
- **Size**: 1,602 bytes
- **Lines**: 42
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testLiquidation from '../../../test/Exchange/base/test.liquidation.js';
import { NetworkError } from '../../../base/errors.js';
async function testWatchLiquidations(exchange, skippedProperties, symbol) {
    // log (symbol.green, 'watching trades...')
    const method = 'watchLiquidations';
    // we have to skip some exchanges here due to the frequency of trading
    const skippedExchanges = [];
    if (exchange.inArray(exchange.id, skippedExchanges)) {
        console.log(exchange.id, method + '() test skipped');
        return false;
    }
    if (!exchange.has[method]) {
        console.log(exchange.id, 'does not support', method + '() method');
        return false;
    }
    let response = undefined;
    let now = Date.now();
    const ends = now + 10000;
    while (now < ends) {
        try {
            response = await exchange[method](symbol);
            now = Date.now();
            const isArray = Array.isArray(response);
            assert(isArray, "response must be an array");
            console.log(exchange.iso8601(now), exchange.id, symbol, method, Object.values(response).length, 'liquidations');
            // log.noLocate (asTable (response))
            for (let i = 0; i < response.length; i++) {
                testLiquidation(exchange, skippedProperties, method, response[i], symbol);
            }
        }
        catch (e) {
            if (!(e instanceof NetworkError)) {
                throw e;
            }
            now = Date.now();
        }
    }
    return response;
}
export default testWatchLiquidations;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchLiquidations.js`.

**Functions defined**: testWatchLiquidations

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 38
- Comment lines: 3
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchLiquidations()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/errors.js` (imported)
- `../../../test/Exchange/base/test.liquidation.js` (imported)
- `assert` (imported)
- `../../../base/errors.js` (referenced)
- `../../../test/Exchange/base/test.liquidation.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchLiquidations.js
```

