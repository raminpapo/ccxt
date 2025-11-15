# Documentation: js/src/static_dependencies/ethers/bytes32.js

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/bytes32.js`
- **Size**: 1,159 bytes
- **Lines**: 40
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
/**
 *  About bytes32 strings...
 *
 *  @_docloc: api/utils:Bytes32 Strings
 */
import { getBytes, toUtf8Bytes, toUtf8String, zeroPadBytes } from "./utils/index.js";
/**
 *  Encodes %%text%% as a Bytes32 string.
 */
export function encodeBytes32String(text) {
    // Get the bytes
    const bytes = toUtf8Bytes(text);
    // Check we have room for null-termination
    if (bytes.length > 31) {
        throw new Error("bytes32 string must be less than 32 bytes");
    }
    // Zero-pad (implicitly null-terminates)
    return zeroPadBytes(bytes, 32);
}
/**
 *  Encodes the Bytes32-encoded %%bytes%% into a string.
 */
export function decodeBytes32String(_bytes) {
    const data = getBytes(_bytes, "bytes");
    // Must be 32 bytes with a null-termination
    if (data.length !== 32) {
        throw new Error("invalid bytes32 - not 32 bytes long");
    }
    if (data[31] !== 0) {
        throw new Error("invalid bytes32 string - no null terminator");
    }
    // Find the null termination
    let length = 31;
    while (data[length - 1] === 0) {
        length--;
    }
    // Determine the string value
    return toUtf8String(data.slice(0, length));
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/ethers/bytes32.js`.

**Functions defined**: encodeBytes32String, decodeBytes32String

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 33
- Comment lines: 17
- Blank lines: -10

### Main Components

**Functions** (2):
- `decodeBytes32String()`
- `encodeBytes32String()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./utils/index.js` (imported)
- `./utils/index.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/ethers/bytes32.js
```

