# Documentation: js/src/test/Exchange/test.fetchMarginModes.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchMarginModes.js`
- **Size**: 982 bytes
- **Lines**: 18
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testMarginMode from './base/test.marginMode.js';
import testSharedMethods from './base/test.sharedMethods.js';
async function testFetchMarginModes(exchange, skippedProperties, symbol) {
    const method = 'fetchMarginModes';
    const marginModes = await exchange.fetchMarginModes(['symbol']);
    assert(typeof marginModes === 'object', exchange.id + ' ' + method + ' ' + symbol + ' must return an object. ' + exchange.json(marginModes));
    const marginModeKeys = Object.keys(marginModes);
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, marginModes, symbol);
    for (let i = 0; i < marginModeKeys.length; i++) {
        const marginMode = marginModes[marginModeKeys[i]];
        testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, marginMode, symbol);
        testMarginMode(exchange, skippedProperties, method, marginMode);
    }
    return true;
}
export default testFetchMarginModes;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchMarginModes.js`.

**Functions defined**: testFetchMarginModes

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 17
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchMarginModes()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `./base/test.marginMode.js` (imported)
- `assert` (imported)
- `./base/test.marginMode.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchMarginModes.js
```

