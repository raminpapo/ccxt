# Documentation: js/src/static_dependencies/ethers/utils/base64.js

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/base64.js`
- **Size**: 1,432 bytes
- **Lines**: 53
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
/**
 *  [Base64 encoding](link-wiki-base64) using 6-bit words to encode
 *  arbitrary bytes into a string using 65 printable symbols, the
 *  upper-case and lower-case alphabet, the digits ``0`` through ``9``,
 *  ``"+"`` and ``"/"`` with the ``"="`` used for padding.
 *
 *  @_subsection: api/utils:Base64 Encoding  [about-base64]
 */
import { getBytes, getBytesCopy } from "./data.js";
/**
 *  Decodes the base-64 encoded %%value%%.
 *
 *  @example:
 *    // The decoded value is always binary data...
 *    result = decodeBase64("SGVsbG8gV29ybGQhIQ==")
 *    //_result:
 *
 *    // ...use toUtf8String to convert it to a string.
 *    toUtf8String(result)
 *    //_result:
 *
 *    // Decoding binary data
 *    decodeBase64("EjQ=")
 *    //_result:
 */
export function decodeBase64(value) {
    return getBytesCopy(Buffer.from(value, "base64"));
}
;
/**
 *  Encodes %%data%% as a base-64 encoded string.
 *
 *  @example:
 *    // Encoding binary data as a hexstring
 *    encodeBase64("0x1234")
 *    //_result:
 *
 *    // Encoding binary data as a Uint8Array
 *    encodeBase64(new Uint8Array([ 0x12, 0x34 ]))
 *    //_result:
 *
 *    // The input MUST be data...
 *    encodeBase64("Hello World!!")
 *    //_error:
 *
 *    // ...use toUtf8Bytes for this.
 *    encodeBase64(toUtf8Bytes("Hello World!!"))
 *    //_result:
 */
export function encodeBase64(data) {
    return Buffer.from(getBytes(data)).toString("base64");
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/ethers/utils/base64.js`.

**Functions defined**: decodeBase64, encodeBase64

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 52
- Comment lines: 44
- Blank lines: -43

### Main Components

**Functions** (2):
- `decodeBase64()`
- `encodeBase64()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./data.js` (imported)
- `./data.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/ethers/utils/base64.js
```

