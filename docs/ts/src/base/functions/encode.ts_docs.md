# Documentation: ts/src/base/functions/encode.ts

## File Metadata

- **Path**: `ts/src/base/functions/encode.ts`
- **Size**: 3,375 bytes
- **Lines**: 96
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/* eslint-disable */
/*  ------------------------------------------------------------------------ */

import { base16, base58, base64, utf8 } from "../../static_dependencies/scure-base/index.js";
import { numberToBytesBE, numberToBytesLE, concatBytes } from '../../static_dependencies/noble-curves/abstract/utils.js';
import { serialize } from '../../static_dependencies/messagepack/msgpack.js'

import qs from '../../static_dependencies/qs/index.js'

/*  ------------------------------------------------------------------------ */

const json =  (data: any, params = undefined) => JSON.stringify (data)
    , isJsonEncodedObject = (object: any) => (
        (typeof object === 'string') &&
        (object.length >= 2) &&
        ((object[0] === '{') || (object[0] === '['))
    )
    , binaryToString = utf8.encode
    , stringToBinary = utf8.decode
    , stringToBase64 = (string: string) => base64.encode (utf8.decode (string))
    , base64ToString = (string: string) => utf8.encode (base64.decode (string))
    , base64ToBinary = base64.decode
    , binaryToBase64 = base64.encode
    , base16ToBinary = base16.decode
    , binaryToBase16 = base16.encode
    , base58ToBinary = base58.decode
    , binaryToBase58 = base58.encode
    , binaryConcat = concatBytes
    , binaryConcatArray = (arr: any[]) => concatBytes (...arr)

    , urlencode = (object: object, sort = false) => qs.stringify (object)
    , urlencodeNested =  (object: object) => qs.stringify (object) // implemented only in python
    , urlencodeWithArrayRepeat = (object: object) => qs.stringify (object, { arrayFormat: 'repeat' })
    , rawencode = (object: object, sort = false) => qs.stringify (object, { encode: false })
    , encode = utf8.decode // lol
    , decode = utf8.encode

    // Url-safe-base64 without equals signs, with + replaced by - and slashes replaced by underscores

    , urlencodeBase64 = (payload: string | Uint8Array) => {
        const payload64 = (typeof payload === 'string') ? stringToBase64 (payload) : binaryToBase64 (payload)
        return payload64.replace (/[=]+$/, '')
            .replace (/\+/g, '-')
            .replace (/\//g, '_')
    }

    , numberToLE = (n: number, padding: number) => numberToBytesLE (BigInt (n), padding)

    , numberToBE = (n: number, padding: number) => numberToBytesBE (BigInt (n), padding)


    function packb(req: any) {
        return serialize(req);
    }

    function base64ToBase64Url(base64: string, stripPadding: boolean = true): string {
        let base64url = base64.replace(/\+/g, "-").replace(/\//g, "_");

        if (stripPadding) {
            base64url = base64url.replace(/=+$/, "");
        }

        return base64url;
    }

export {
    json
    , isJsonEncodedObject
    , binaryToString
    , stringToBinary
    , stringToBase64
    , base64ToBinary
    , base64ToString
    , binaryToBase64
    , base16ToBinary
    , binaryToBase16
    , binaryConcat
    , binaryConcatArray
    , base64ToBase64Url
    , urlencode
    , urlencodeWithArrayRepeat
    , rawencode
    , encode
    , decode
    // Url-safe-base64 without equals signs, with + replaced by - and slashes replaced by underscores
    , urlencodeBase64
    , numberToLE
    , numberToBE
    , base58ToBinary
    , binaryToBase58
    , urlencodeNested
    , packb
}

/*  ------------------------------------------------------------------------ */

```

## High-Level Overview

This is a TypeScript file located at `ts/src/base/functions/encode.ts`.

**Functions defined**: packb, base64ToBase64Url

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 96
- Code lines: 77
- Comment lines: 6
- Blank lines: 13

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

**To execute this TypeScript file:**

```bash
ts-node ts/src/base/functions/encode.ts
```

