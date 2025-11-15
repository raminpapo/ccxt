# Documentation: ts/src/test/base/test.removeRepeatedElementsFromArray.ts

## File Metadata

- **Path**: `ts/src/test/base/test.removeRepeatedElementsFromArray.ts`
- **Size**: 1,802 bytes
- **Lines**: 54
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// AUTO_TRANSPILE_ENABLED

import assert from 'assert';
import ccxt from '../../../ccxt.js';

function testRemoveRepeatedElementsFromArray () {

    const exchange = new ccxt.Exchange ({
        'id': 'sampleexchange',
    });

    // CASE 1: by id
    const array1 = [
        { 'id': 'a', 'timestamp': 1, 'uniq': 'x1' },
        { 'id': 'b', 'timestamp': 2, 'uniq': 'x2' },
        { 'id': 'a', 'timestamp': 3, 'uniq': 'x3' }, // duplicate id
        { 'id': 'c', 'timestamp': 1, 'uniq': 'x4' }, // duplicate timestamp
    ];
    const res1 = exchange.removeRepeatedElementsFromArray (array1, false);
    const res1Length = res1.length;
    assert (res1Length === 3);
    assert (res1[0]['uniq'] === 'x1');
    assert (res1[1]['uniq'] === 'x2');
    assert (res1[2]['uniq'] === 'x4');

    // CASE 2: by timestamp
    const array2 = [
        { 'id': undefined, 'timestamp': 1, 'uniq': 'x1' },
        { 'id': undefined, 'timestamp': 2, 'uniq': 'x2' },
        { 'id': undefined, 'timestamp': 1, 'uniq': 'x3' }, // duplicate timestamp
        { 'id': undefined, 'timestamp': 3, 'uniq': 'x4' },
    ];
    const res2 = exchange.removeRepeatedElementsFromArray (array2, true);
    const res2Length = res2.length;
    assert (res2Length === 3);
    assert (res2[0]['uniq'] === 'x1');
    assert (res2[1]['uniq'] === 'x2');
    assert (res2[2]['uniq'] === 'x4');

    // CASE 3: by timestamp index (used in ohlcv)
    const array3 = [
        [ 555, 1.0, 1.0, "x1" ],
        [ 666, 1.0, 1.0, "x2" ],
        [ 555, 1.0, 1.0, "x3" ], // duplicate timestamp (0 index)
    ];
    const res3 = exchange.removeRepeatedElementsFromArray (array3, true);
    assert (res3.length === 2);
    assert (res3[0][3] === "x1");
    assert (res3[1][3] === "x2");
}

export default testRemoveRepeatedElementsFromArray;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/test.removeRepeatedElementsFromArray.ts`.

**Functions defined**: testRemoveRepeatedElementsFromArray

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 41
- Comment lines: 4
- Blank lines: 9

### Main Components

**Functions** (1):
- `testRemoveRepeatedElementsFromArray()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/test.removeRepeatedElementsFromArray.ts
```

