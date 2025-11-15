# Documentation: js/src/base/functions/encode.js

## File Metadata

- **Path**: `js/src/base/functions/encode.js`
- **Size**: 2,876 bytes
- **Lines**: 34
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
/* eslint-disable */
/*  ------------------------------------------------------------------------ */
import { base16, base58, base64, utf8 } from "../../static_dependencies/scure-base/index.js";
import { numberToBytesBE, numberToBytesLE, concatBytes } from '../../static_dependencies/noble-curves/abstract/utils.js';
import { serialize } from '../../static_dependencies/messagepack/msgpack.js';
import qs from '../../static_dependencies/qs/index.js';
/*  ------------------------------------------------------------------------ */
const json = (data, params = undefined) => JSON.stringify(data), isJsonEncodedObject = (object) => ((typeof object === 'string') &&
    (object.length >= 2) &&
    ((object[0] === '{') || (object[0] === '['))), binaryToString = utf8.encode, stringToBinary = utf8.decode, stringToBase64 = (string) => base64.encode(utf8.decode(string)), base64ToString = (string) => utf8.encode(base64.decode(string)), base64ToBinary = base64.decode, binaryToBase64 = base64.encode, base16ToBinary = base16.decode, binaryToBase16 = base16.encode, base58ToBinary = base58.decode, binaryToBase58 = base58.encode, binaryConcat = concatBytes, binaryConcatArray = (arr) => concatBytes(...arr), urlencode = (object, sort = false) => qs.stringify(object), urlencodeNested = (object) => qs.stringify(object) // implemented only in python
, urlencodeWithArrayRepeat = (object) => qs.stringify(object, { arrayFormat: 'repeat' }), rawencode = (object, sort = false) => qs.stringify(object, { encode: false }), encode = utf8.decode // lol
, decode = utf8.encode
// Url-safe-base64 without equals signs, with + replaced by - and slashes replaced by underscores
, urlencodeBase64 = (payload) => {
    const payload64 = (typeof payload === 'string') ? stringToBase64(payload) : binaryToBase64(payload);
    return payload64.replace(/[=]+$/, '')
        .replace(/\+/g, '-')
        .replace(/\//g, '_');
}, numberToLE = (n, padding) => numberToBytesLE(BigInt(n), padding), numberToBE = (n, padding) => numberToBytesBE(BigInt(n), padding);
function packb(req) {
    return serialize(req);
}
function base64ToBase64Url(base64, stripPadding = true) {
    let base64url = base64.replace(/\+/g, "-").replace(/\//g, "_");
    if (stripPadding) {
        base64url = base64url.replace(/=+$/, "");
    }
    return base64url;
}
export { json, isJsonEncodedObject, binaryToString, stringToBinary, stringToBase64, base64ToBinary, base64ToString, binaryToBase64, base16ToBinary, binaryToBase16, binaryConcat, binaryConcatArray, base64ToBase64Url, urlencode, urlencodeWithArrayRepeat, rawencode, encode, decode
// Url-safe-base64 without equals signs, with + replaced by - and slashes replaced by underscores
, urlencodeBase64, numberToLE, numberToBE, base58ToBinary, binaryToBase58, urlencodeNested, packb };
/*  ------------------------------------------------------------------------ */

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/functions/encode.js`.

**Functions defined**: packb, base64ToBase64Url

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 31
- Comment lines: 6
- Blank lines: -3

### Main Components

**Functions** (2):
- `base64ToBase64Url()`
- `packb()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../static_dependencies/messagepack/msgpack.js` (imported)
- `../../static_dependencies/noble-curves/abstract/utils.js` (imported)
- `../../static_dependencies/qs/index.js` (imported)
- `../../static_dependencies/scure-base/index.js` (imported)
- `../../static_dependencies/messagepack/msgpack.js` (referenced)
- `../../static_dependencies/noble-curves/abstract/utils.js` (referenced)
- `../../static_dependencies/qs/index.js` (referenced)
- `../../static_dependencies/scure-base/index.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/functions/encode.js
```

