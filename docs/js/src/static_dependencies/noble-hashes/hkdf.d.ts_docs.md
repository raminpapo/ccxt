# Documentation: js/src/static_dependencies/noble-hashes/hkdf.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/hkdf.d.ts`
- **Size**: 1,226 bytes
- **Lines**: 27
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { CHash, Input } from './utils.js';
/**
 * HKDF-Extract(IKM, salt) -> PRK
 * Arguments position differs from spec (IKM is first one, since it is not optional)
 * @param hash
 * @param ikm
 * @param salt
 * @returns
 */
export declare function extract(hash: CHash, ikm: Input, salt?: Input): Uint8Array;
/**
 * HKDF-expand from the spec.
 * @param prk - a pseudorandom key of at least HashLen octets (usually, the output from the extract step)
 * @param info - optional context and application specific information (can be a zero-length string)
 * @param length - length of output keying material in octets
 */
export declare function expand(hash: CHash, prk: Input, info?: Input, length?: number): Uint8Array;
/**
 * HKDF (RFC 5869): extract + expand in one step.
 * @param hash - hash function that would be used (e.g. sha256)
 * @param ikm - input keying material, the initial key
 * @param salt - optional salt value (a non-secret random value)
 * @param info - optional context and application specific information
 * @param length - length of output keying material in octets
 */
export declare const hkdf: (hash: CHash, ikm: Input, salt: Input | undefined, info: Input | undefined, length: number) => Uint8Array;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/hkdf.d.ts`.

**Functions defined**: expand, extract, that

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 26
- Comment lines: 22
- Blank lines: -21

### Main Components

**Functions** (3):
- `expand()`
- `extract()`
- `that()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./utils.js` (imported)
- `./utils.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-hashes/hkdf.d.ts
```

