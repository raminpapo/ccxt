# Documentation: js/src/pro/test/Exchange/test.watchBalance.js

## File Metadata

- **Path**: `js/src/pro/test/Exchange/test.watchBalance.js`
- **Size**: 940 bytes
- **Lines**: 29
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testBalance from '../../../test/Exchange/base/test.balance.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';
async function testWatchBalance(exchange, skippedProperties, code) {
    const method = 'watchBalance';
    let now = exchange.milliseconds();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchBalance();
        }
        catch (e) {
            if (!testSharedMethods.isTemporaryFailure(e)) {
                throw e;
            }
            now = exchange.milliseconds();
            // continue;
            success = false;
        }
        if (success === false) {
            continue; // retry
        }
        testBalance(exchange, skippedProperties, method, response);
        now = exchange.milliseconds();
    }
}
export default testWatchBalance;

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/test/Exchange/test.watchBalance.js`.

**Functions defined**: testWatchBalance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 27
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `testWatchBalance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../test/Exchange/base/test.balance.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../test/Exchange/base/test.balance.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/pro/test/Exchange/test.watchBalance.js
```

