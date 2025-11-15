# Documentation: js/src/pro/test/Exchange/test.watchBidsAsks.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchBidsAsks.js`
- **Size**: 2,661 bytes
- **Lines**: 58
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testTicker from '../../../test/Exchange/base/test.ticker.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
import { ArgumentsRequired } from '../../../base/errors.js';
async function testWatchBidsAsks(exchange, skippedProperties, symbol) {
    const withoutSymbol = testWatchBidsAsksHelper(exchange, skippedProperties, undefined);
    const withSymbol = testWatchBidsAsksHelper(exchange, skippedProperties, [symbol]);
    await Promise.all([withSymbol, withoutSymbol]);
}
async function testWatchBidsAsksHelper(exchange, skippedProperties, argSymbols, argParams = {}) {
    const method = 'watchBidsAsks';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let success = true;
        let shouldReturn = false;
        let response = undefined;
        try {
            response = await exchange.watchBidsAsks(argSymbols, argParams);
        }
        catch (e) {
            // for some exchanges, multi symbol methods might require symbols array to be present, so
            // so, if method throws "arguments-required" exception, we don't fail test, but just skip silently,
            // because tests will make a second call of this method with symbols array
            if ((e instanceof ArgumentsRequired) && (argSymbols === undefined || argSymbols.length === 0)) {
                // todo: provide random symbols to try
                // return false;
                shouldReturn = true;
            }
            else if (!testSharedMethods.isTemporaryFailure(e)) {
                throw e;
            }
            now = exchange.milliseconds();
            // continue;
            success = false;
        }
        if (shouldReturn) {
            return false;
        }
        if (success === true) {
            assert(typeof response === 'object', exchange.id + ' ' + method + ' ' + exchange.json(argSymbols) + ' must return an object. ' + exchange.json(response));
            const values = Object.values(response);
            let checkedSymbol = undefined;
            if (argSymbols !== undefined && argSymbols.length === 1) {
                checkedSymbol = argSymbols[0];
            }
            testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, values, checkedSymbol);
            for (let i = 0; i < values.length; i++) {
                const ticker = values[i];
                testTicker(exchange, skippedProperties, method, ticker, checkedSymbol);
            }
            now = exchange.milliseconds();
        }
    }
    return true;
}
export default testWatchBidsAsks;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchBidsAsks.js`.

**Functions defined**: testWatchBidsAsksHelper, testWatchBidsAsks

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 51
- Comment lines: 6
- Blank lines: 1

### Main Components

**Functions** (2):
- `testWatchBidsAsks()`
- `testWatchBidsAsksHelper()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/errors.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../test/Exchange/base/test.ticker.js` (imported)
- `assert` (imported)
- `../../../base/errors.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../test/Exchange/base/test.ticker.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchBidsAsks.js
```

