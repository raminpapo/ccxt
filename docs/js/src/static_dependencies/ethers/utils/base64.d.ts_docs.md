# Documentation: js/src/static_dependencies/ethers/utils/base64.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/base64.d.ts`
- **Size**: 1,021 bytes
- **Lines**: 40
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import type { BytesLike } from "./data.js";
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
export declare function decodeBase64(value: string): Uint8Array;
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
export declare function encodeBase64(data: BytesLike): string;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/utils/base64.d.ts`.

**Functions defined**: decodeBase64, encodeBase64

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 39
- Comment lines: 36
- Blank lines: -35

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

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/utils/base64.d.ts
```

