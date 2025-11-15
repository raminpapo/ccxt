# Documentation: ts/src/test/base/language_specific/test.legacyHas.ts

## File Metadata

- **Path**: `ts/src/test/base/language_specific/test.legacyHas.ts`
- **Size**: 612 bytes
- **Lines**: 28
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// @ts-nocheck

import assert, { strictEqual, deepEqual } from 'assert';
import ccxt, { Exchange, functions } from '../../../../ccxt.js';

const { index, aggregate, unCamelCase } = functions;

const equal = strictEqual;


function testLegacyHas () {

    const exchange = new Exchange ({
        'id': 'mock',
        'has': {
            'CORS': true,
            'publicAPI': false,
            'fetchDepositAddress': 'emulated'
        }
    });

    equal (exchange.hasCORS, true);
    equal (exchange.hasPublicAPI, false);
    equal (exchange.hasFetchDepositAddress, true);
}

export default testLegacyHas;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/language_specific/test.legacyHas.ts`.

**Functions defined**: testLegacyHas

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 18
- Comment lines: 1
- Blank lines: 9

### Main Components

**Functions** (1):
- `testLegacyHas()`



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
npm test ts/src/test/base/language_specific/test.legacyHas.ts
```

