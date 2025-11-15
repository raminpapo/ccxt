# Documentation: js/src/static_dependencies/noble-hashes/pbkdf2.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/pbkdf2.d.ts`
- **Size**: 668 bytes
- **Lines**: 16
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { CHash, Input } from './utils.js';
export declare type Pbkdf2Opt = {
    c: number;
    dkLen?: number;
    asyncTick?: number;
};
/**
 * PBKDF2-HMAC: RFC 2898 key derivation function
 * @param hash - hash function that would be used e.g. sha256
 * @param password - password from which a derived key is generated
 * @param salt - cryptographic salt
 * @param opts - {c, dkLen} where c is work factor and dkLen is output message size
 */
export declare function pbkdf2(hash: CHash, password: Input, salt: Input, opts: Pbkdf2Opt): Uint8Array;
export declare function pbkdf2Async(hash: CHash, password: Input, salt: Input, opts: Pbkdf2Opt): Promise<Uint8Array>;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/pbkdf2.d.ts`.

**Functions defined**: that, pbkdf2, pbkdf2Async

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 15
- Comment lines: 7
- Blank lines: -6

### Main Components

**Functions** (3):
- `pbkdf2()`
- `pbkdf2Async()`
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
ts-node js/src/static_dependencies/noble-hashes/pbkdf2.d.ts
```

