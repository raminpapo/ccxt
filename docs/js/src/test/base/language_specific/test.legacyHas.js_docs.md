# Documentation: js/src/test/base/language_specific/test.legacyHas.js

## File Metadata

- **Path**: `js/src/test/base/language_specific/test.legacyHas.js`
- **Size**: 574 bytes
- **Lines**: 20
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// @ts-nocheck
import { strictEqual } from 'assert';
import { Exchange, functions } from '../../../../ccxt.js';
const { index, aggregate, unCamelCase } = functions;
const equal = strictEqual;
function testLegacyHas() {
    const exchange = new Exchange({
        'id': 'mock',
        'has': {
            'CORS': true,
            'publicAPI': false,
            'fetchDepositAddress': 'emulated'
        }
    });
    equal(exchange.hasCORS, true);
    equal(exchange.hasPublicAPI, false);
    equal(exchange.hasFetchDepositAddress, true);
}
export default testLegacyHas;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/language_specific/test.legacyHas.js`.

**Functions defined**: testLegacyHas

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 18
- Comment lines: 1
- Blank lines: 1

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
npm test js/src/test/base/language_specific/test.legacyHas.js
```

