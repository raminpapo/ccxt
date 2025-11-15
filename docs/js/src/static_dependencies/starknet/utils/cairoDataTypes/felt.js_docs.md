# Documentation: js/src/static_dependencies/starknet/utils/cairoDataTypes/felt.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/cairoDataTypes/felt.js`
- **Size**: 1,295 bytes
- **Lines**: 38
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// TODO Convert to CairoFelt base on CairoUint256 and implement it in the codebase in the backward compatible manner
import { isBigInt, isBoolean, isHex, isStringWholeNumber } from '../num.js';
import { encodeShortString, isShortString, isString, isText } from '../shortString.js';
/**
 * Create felt Cairo type (cairo type helper)
 * @returns format: felt-string
 */
export function CairoFelt(it) {
    // BN or number
    if (isBigInt(it) || Number.isInteger(it)) {
        return it.toString();
    }
    // Handling strings
    if (isString(it)) {
        // Hex strings
        if (isHex(it)) {
            return BigInt(it).toString();
        }
        // Text strings that must be short
        if (isText(it)) {
            if (!isShortString(it)) {
                throw new Error(`${it} is a long string > 31 chars. Please split it into an array of short strings.`);
            }
            // Assuming encodeShortString returns a hex representation of the string
            return BigInt(encodeShortString(it)).toString();
        }
        // Whole numeric strings
        if (isStringWholeNumber(it)) {
            return it;
        }
    }
    // bool to felt
    if (isBoolean(it)) {
        return `${+it}`;
    }
    throw new Error(`${it} can't be computed by felt()`);
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/cairoDataTypes/felt.js`.

**Functions defined**: CairoFelt

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 29
- Comment lines: 12
- Blank lines: -3

### Main Components

**Functions** (1):
- `CairoFelt()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../num.js` (imported)
- `../shortString.js` (imported)
- `../num.js` (referenced)
- `../shortString.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/cairoDataTypes/felt.js
```

