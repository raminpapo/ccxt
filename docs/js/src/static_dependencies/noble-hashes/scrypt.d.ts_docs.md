# Documentation: js/src/static_dependencies/noble-hashes/scrypt.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/scrypt.d.ts`
- **Size**: 1,126 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Input } from './utils.js';
export declare type ScryptOpts = {
    N: number;
    r: number;
    p: number;
    dkLen?: number;
    asyncTick?: number;
    maxmem?: number;
    onProgress?: (progress: number) => void;
};
/**
 * Scrypt KDF from RFC 7914.
 * @param password - pass
 * @param salt - salt
 * @param opts - parameters
 * - `N` is cpu/mem work factor (power of 2 e.g. 2**18)
 * - `r` is block size (8 is common), fine-tunes sequential memory read size and performance
 * - `p` is parallelization factor (1 is common)
 * - `dkLen` is output key length in bytes e.g. 32.
 * - `asyncTick` - (default: 10) max time in ms for which async function can block execution
 * - `maxmem` - (default: `1024 ** 3 + 1024` aka 1GB+1KB). A limit that the app could use for scrypt
 * - `onProgress` - callback function that would be executed for progress report
 * @returns Derived key
 */
export declare function scrypt(password: Input, salt: Input, opts: ScryptOpts): Uint8Array;
/**
 * Scrypt KDF from RFC 7914.
 */
export declare function scryptAsync(password: Input, salt: Input, opts: ScryptOpts): Promise<Uint8Array>;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/scrypt.d.ts`.

**Functions defined**: that, can, scryptAsync, scrypt

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 29
- Comment lines: 17
- Blank lines: -16

### Main Components

**Functions** (4):
- `can()`
- `scrypt()`
- `scryptAsync()`
- `that()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./utils.js` (imported)
- `./utils.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-hashes/scrypt.d.ts
```

