# Documentation: ts/src/test/base/language_specific/test.aggregate.ts

## File Metadata

- **Path**: `ts/src/test/base/language_specific/test.aggregate.ts`
- **Size**: 972 bytes
- **Lines**: 44
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// @ts-nocheck
// todo: per https://github.com/ttodua/ccxt/blob/428f5b50da50b7401caa5ac452538fb0f6641af4/ts/src/test/base/test.aggregate.ts

import assert, { strictEqual, deepEqual } from 'assert';
import ccxt, { Exchange, functions } from '../../../../ccxt.js';

const { index, aggregate, unCamelCase } = functions;

const equal = strictEqual;


function testAggregate () {

    const bids = [
        [ 789.1, 123.0 ],
        [ 789.100, 123.0 ],
        [ 123.0, 456.0 ],
        [ 789.0, 123.0 ],
        [ 789.10, 123.0 ],
    ];

    const asks = [
        [ 123.0, 456.0 ],
        [ 789.0, 123.0 ],
        [ 789.10, 123.0 ],
    ];

    deepEqual (aggregate (bids.sort ()), [
        [ 123.0, 456.0 ],
        [ 789.0, 123.0 ],
        [ 789.1, 369.0 ],
    ]);

    deepEqual (aggregate (asks.sort ()), [
        [ 123.0, 456.0 ],
        [ 789.0, 123.0 ],
        [ 789.10, 123.0 ],
    ]);

    deepEqual (aggregate ([]), []);
}

export default testAggregate;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/language_specific/test.aggregate.ts`.

**Functions defined**: testAggregate

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 30
- Comment lines: 2
- Blank lines: 12

### Main Components

**Functions** (1):
- `testAggregate()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/language_specific/test.aggregate.ts
```

