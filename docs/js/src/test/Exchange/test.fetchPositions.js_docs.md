# Documentation: js/src/test/Exchange/test.fetchPositions.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.fetchPositions.js`
- **Size**: 1,566 bytes
- **Lines**: 26
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import assert from 'assert';
import testPosition from './base/test.position.js';
import testSharedMethods from '../../test/Exchange/base/test.sharedMethods.js';
async function testFetchPositions(exchange, skippedProperties, symbol) {
    const method = 'fetchPositions';
    const now = exchange.milliseconds();
    // without symbol
    const positions = await exchange.fetchPositions();
    testSharedMethods.assertNonEmtpyArray(exchange, skippedProperties, method, positions, symbol);
    for (let i = 0; i < positions.length; i++) {
        testPosition(exchange, skippedProperties, method, positions[i], undefined, now);
    }
    // testSharedMethods.assertTimestampOrder (exchange, method, undefined, positions); // currently order of positions does not make sense
    // with symbol
    const positionsForSymbol = await exchange.fetchPositions([symbol]);
    assert(Array.isArray(positionsForSymbol), exchange.id + ' ' + method + ' must return an array, returned ' + exchange.json(positionsForSymbol));
    const positionsForSymbolLength = positionsForSymbol.length;
    assert(positionsForSymbolLength <= 4, exchange.id + ' ' + method + ' positions length for particular symbol should be less than 4, returned ' + exchange.json(positionsForSymbol));
    for (let i = 0; i < positionsForSymbol.length; i++) {
        testPosition(exchange, skippedProperties, method, positionsForSymbol[i], symbol, now);
    }
    // testSharedMethods.assertTimestampOrder (exchange, method, symbol, positionsForSymbol);
    return true;
}
export default testFetchPositions;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.fetchPositions.js`.

**Functions defined**: testFetchPositions

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 21
- Comment lines: 4
- Blank lines: 1

### Main Components

**Functions** (1):
- `testFetchPositions()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../test/Exchange/base/test.sharedMethods.js` (imported)
- `./base/test.position.js` (imported)
- `assert` (imported)
- `../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `./base/test.position.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.fetchPositions.js
```

