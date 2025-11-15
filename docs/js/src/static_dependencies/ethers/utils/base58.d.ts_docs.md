# Documentation: js/src/static_dependencies/ethers/utils/base58.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/base58.d.ts`
- **Size**: 837 bytes
- **Lines**: 23
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 *  The [Base58 Encoding](link-base58) scheme allows a **numeric** value
 *  to be encoded as a compact string using a radix of 58 using only
 *  alpha-numeric characters. Confusingly similar characters are omitted
 *  (i.e. ``"l0O"``).
 *
 *  Note that Base58 encodes a **numeric** value, not arbitrary bytes,
 *  since any zero-bytes on the left would get removed. To mitigate this
 *  issue most schemes that use Base58 choose specific high-order values
 *  to ensure non-zero prefixes.
 *
 *  @_subsection: api/utils:Base58 Encoding [about-base58]
 */
import type { BytesLike } from "./index.js";
/**
 *  Encode %%value%% as a Base58-encoded string.
 */
export declare function encodeBase58(_value: BytesLike): string;
/**
 *  Decode the Base58-encoded %%value%%.
 */
export declare function decodeBase58(value: string): bigint;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/utils/base58.d.ts`.

**Functions defined**: encodeBase58, decodeBase58

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 22
- Comment lines: 19
- Blank lines: -18

### Main Components

**Functions** (2):
- `decodeBase58()`
- `encodeBase58()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./index.js` (imported)
- `./index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/utils/base58.d.ts
```

