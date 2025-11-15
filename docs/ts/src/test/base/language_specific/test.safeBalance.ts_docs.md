# Documentation: ts/src/test/base/language_specific/test.safeBalance.ts

## File Metadata

- **Path**: `ts/src/test/base/language_specific/test.safeBalance.ts`
- **Size**: 1,045 bytes
- **Lines**: 47
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// @ts-nocheck

import assert, { strictEqual, deepEqual } from 'assert';
import ccxt, { Exchange, functions } from '../../../../ccxt.js';

const { index, aggregate, unCamelCase } = functions;

const equal = strictEqual;


function testSafeBalance () {

    const exchange = new Exchange ({
        'markets': {
            'ETH/BTC': { 'id': 'ETH/BTC', 'symbol': 'ETH/BTC', 'base': 'ETH', 'quote': 'BTC', }
        }
    });

    const input = {
        'ETH': { 'free': 10, 'used': 10, 'total': 20 },
        'ZEC': { 'free': 0, 'used': 0, 'total': 0 },
    };

    const expected = {
        'ETH': { 'free': 10, 'used': 10, 'total': 20 },
        'ZEC': { 'free': 0, 'used': 0, 'total': 0 },
        'free': {
            'ETH': 10,
            'ZEC': 0,
        },
        'used': {
            'ETH': 10,
            'ZEC': 0,
        },
        'total': {
            'ETH': 20,
            'ZEC': 0,
        },
    };

    const actual = exchange.safeBalance (input);

    deepEqual (actual, expected);
}

export default testSafeBalance;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/language_specific/test.safeBalance.ts`.

**Functions defined**: testSafeBalance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 34
- Comment lines: 1
- Blank lines: 12

### Main Components

**Functions** (1):
- `testSafeBalance()`



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
npm test ts/src/test/base/language_specific/test.safeBalance.ts
```

