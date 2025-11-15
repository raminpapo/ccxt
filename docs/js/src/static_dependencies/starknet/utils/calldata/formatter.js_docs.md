# Documentation: js/src/static_dependencies/starknet/utils/calldata/formatter.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/formatter.js`
- **Size**: 2,272 bytes
- **Lines**: 62
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { isBigInt } from '../num.js';
import { decodeShortString } from '../shortString.js';
const guard = {
    isBN: (data, type, key) => {
        if (!isBigInt(data[key]))
            throw new Error(`Data and formatter mismatch on ${key}:${type[key]}, expected response data ${key}:${data[key]} to be BN instead it is ${typeof data[key]}`);
    },
    unknown: (data, type, key) => {
        throw new Error(`Unhandled formatter type on ${key}:${type[key]} for data ${key}:${data[key]}`);
    },
};
/**
 * Formats the given data based on the provided type definition.
 *
 * @param {any} data - The data to be formatted.
 * @param {any} type - The type definition for the data.
 * @param {any} [sameType] - The same type definition to be used (optional).
 * @returns - The formatted data.
 */
export default function formatter(data, type, sameType) {
    // match data element with type element
    return Object.entries(data).reduce((acc, [key, value]) => {
        const elType = sameType ?? type[key];
        if (!(key in type) && !sameType) {
            // no type definition for element return original element
            acc[key] = value;
            return acc;
        }
        if (elType === 'string') {
            if (Array.isArray(data[key])) {
                // long string (felt*)
                const arrayStr = formatter(data[key], data[key].map((_) => elType));
                acc[key] = Object.values(arrayStr).join('');
                return acc;
            }
            guard.isBN(data, type, key);
            acc[key] = decodeShortString(value);
            return acc;
        }
        if (elType === 'number') {
            guard.isBN(data, type, key);
            acc[key] = Number(value);
            return acc;
        }
        if (typeof elType === 'function') {
            acc[key] = elType(value);
            return acc;
        }
        if (Array.isArray(elType)) {
            const arrayObj = formatter(data[key], elType, elType[0]);
            acc[key] = Object.values(arrayObj);
            return acc;
        }
        if (typeof elType === 'object') {
            acc[key] = formatter(data[key], elType);
            return acc;
        }
        guard.unknown(data, type, key);
        return acc;
    }, {});
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/formatter.js`.

**Functions defined**: formatter

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 58
- Comment lines: 11
- Blank lines: -7

### Main Components

**Functions** (1):
- `formatter()`



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
node js/src/static_dependencies/starknet/utils/calldata/formatter.js
```

