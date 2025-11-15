# Documentation: ts/src/test/base/test.filterBy.ts

## File Metadata

- **Path**: `ts/src/test/base/test.filterBy.ts`
- **Size**: 879 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// AUTO_TRANSPILE_ENABLED

import assert from 'assert';
import ccxt from '../../../ccxt.js';
import testSharedMethods from '../Exchange/base/test.sharedMethods.js';

function testFilterBy () {

    const exchange = new ccxt.Exchange ({
        'id': 'sampleexchange',
    });

    const sampleArray = [
        { 'foo': 'a' },
        { 'foo': undefined },
        { 'foo': 'b' },
        // { }, todo : bugs in py
        { 'foo': 'a', 'bar': 'b' },
        { 'foo': 'c' },
        { 'foo': 'd' },
        { 'foo': 'b' },
        { 'foo': 'c' },
        { 'foo': 'c' },
    ];

    const currentValue = exchange.filterBy (sampleArray, 'foo', 'a');
    const storedValue = [
        { 'foo': 'a' },
        { 'foo': 'a', 'bar': 'b' },
    ];
    testSharedMethods.assertDeepEqual (exchange, undefined, 'testFilterBy', currentValue, storedValue);
}

export default testFilterBy;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/test.filterBy.ts`.

**Functions defined**: testFilterBy

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 26
- Comment lines: 2
- Blank lines: 8

### Main Components

**Functions** (1):
- `testFilterBy()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../Exchange/base/test.sharedMethods.js` (imported)
- `../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../ccxt.js` (referenced)
- `../Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/test.filterBy.ts
```

