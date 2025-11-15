# Documentation: js/src/pro/test/Exchange/test.watchPosition.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchPosition.js`
- **Size**: 1,141 bytes
- **Lines**: 31
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testPosition from '../../../test/Exchange/base/test.position.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchPosition(exchange, skippedProperties, symbol) {
    const method = 'watchPosition';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchPosition(symbol);
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
            assert(typeof response === 'object', exchange.id + ' ' + method + ' ' + symbol + ' must return an object. ' + exchange.json(response));
            now = exchange.milliseconds();
            testPosition(exchange, skippedProperties, method, response, undefined, now);
        }
    }
    return true;
}
export default testWatchPosition;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchPosition.js`.

**Functions defined**: testWatchPosition

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 29
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchPosition()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.position.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `assert` (imported)
- `../../../test/Exchange/base/test.position.js` (referenced)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchPosition.js
```

