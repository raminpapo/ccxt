# Documentation: js/src/test/base/language_specific/test.safeBalance.js

## File Metadata

- **Path**: `js/src/test/base/language_specific/test.safeBalance.js`
- **Size**: 1,016 bytes
- **Lines**: 36
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// @ts-nocheck
import { strictEqual, deepEqual } from 'assert';
import { Exchange, functions } from '../../../../ccxt.js';
const { index, aggregate, unCamelCase } = functions;
const equal = strictEqual;
function testSafeBalance() {
    const exchange = new Exchange({
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
    const actual = exchange.safeBalance(input);
    deepEqual(actual, expected);
}
export default testSafeBalance;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/language_specific/test.safeBalance.js`.

**Functions defined**: testSafeBalance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 34
- Comment lines: 1
- Blank lines: 1

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
npm test js/src/test/base/language_specific/test.safeBalance.js
```

