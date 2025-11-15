# Documentation: js/src/base/functions/encode.d.ts

## File Metadata

- **Path**: `js/src/base/functions/encode.d.ts`
- **Size**: 1,689 bytes
- **Lines**: 6
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { concatBytes } from '../../static_dependencies/noble-curves/abstract/utils.js';
declare const json: (data: any, params?: any) => string, isJsonEncodedObject: (object: any) => boolean, binaryToString: (data: Uint8Array) => string, stringToBinary: (str: string) => Uint8Array, stringToBase64: (string: string) => string, base64ToString: (string: string) => string, base64ToBinary: (str: string) => Uint8Array, binaryToBase64: (data: Uint8Array) => string, base16ToBinary: (str: string) => Uint8Array, binaryToBase16: (data: Uint8Array) => string, base58ToBinary: (str: string) => Uint8Array, binaryToBase58: (data: Uint8Array) => string, binaryConcat: typeof concatBytes, binaryConcatArray: (arr: any[]) => Uint8Array, urlencode: (object: object, sort?: boolean) => string, urlencodeNested: (object: object) => string, urlencodeWithArrayRepeat: (object: object) => string, rawencode: (object: object, sort?: boolean) => string, encode: (str: string) => Uint8Array, decode: (data: Uint8Array) => string, urlencodeBase64: (payload: string | Uint8Array) => string, numberToLE: (n: number, padding: number) => Uint8Array, numberToBE: (n: number, padding: number) => Uint8Array;
declare function packb(req: any): Uint8Array;
declare function base64ToBase64Url(base64: string, stripPadding?: boolean): string;
export { json, isJsonEncodedObject, binaryToString, stringToBinary, stringToBase64, base64ToBinary, base64ToString, binaryToBase64, base16ToBinary, binaryToBase16, binaryConcat, binaryConcatArray, base64ToBase64Url, urlencode, urlencodeWithArrayRepeat, rawencode, encode, decode, urlencodeBase64, numberToLE, numberToBE, base58ToBinary, binaryToBase58, urlencodeNested, packb };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/encode.d.ts`.

**Functions defined**: packb, base64ToBase64Url

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 6
- Code lines: 5
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `base64ToBase64Url()`
- `packb()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../static_dependencies/noble-curves/abstract/utils.js` (imported)
- `../../static_dependencies/noble-curves/abstract/utils.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/functions/encode.d.ts
```

