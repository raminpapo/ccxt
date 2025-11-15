# Documentation: ts/src/test/base/test.groupBy.ts

## File Metadata

- **Path**: `ts/src/test/base/test.groupBy.ts`
- **Size**: 804 bytes
- **Lines**: 32
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// AUTO_TRANSPILE_ENABLED

import ccxt from '../../../ccxt.js';
import testSharedMethods from '../Exchange/base/test.sharedMethods.js';

function testGroupBy () {

    const exchange = new ccxt.Exchange ({
        'id': 'sampleexchange',
    });

    const sampleArray = [
        { 'foo': 'a' },
        { 'foo': 'b' },
        { 'foo': 'c' },
        { 'foo': 'b' },
        { 'foo': 'c' },
        { 'foo': 'c' },
    ];

    const currentValue = exchange.groupBy (sampleArray, 'foo');
    const storedValue = {
        'a': [ { 'foo': 'a' } ],
        'b': [ { 'foo': 'b' }, { 'foo': 'b' } ],
        'c': [ { 'foo': 'c' }, { 'foo': 'c' }, { 'foo': 'c' } ],
    };
    testSharedMethods.assertDeepEqual (exchange, undefined, 'testGroupBy', currentValue, storedValue);
}

export default testGroupBy;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/test.groupBy.ts`.

**Functions defined**: testGroupBy

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 23
- Comment lines: 1
- Blank lines: 8

### Main Components

**Functions** (1):
- `testGroupBy()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../ccxt.js` (imported)
- `../Exchange/base/test.sharedMethods.js` (imported)
- `../../../ccxt.js` (referenced)
- `../Exchange/base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/test.groupBy.ts
```

