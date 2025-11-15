# Documentation: js/src/static_dependencies/noble-hashes/blake2s.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/blake2s.d.ts`
- **Size**: 1,602 bytes
- **Lines**: 48
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BLAKE2, BlakeOpts } from './_blake2.js';
export declare const IV: Uint32Array;
export declare function compress(s: Uint8Array, offset: number, msg: Uint32Array, rounds: number, v0: number, v1: number, v2: number, v3: number, v4: number, v5: number, v6: number, v7: number, v8: number, v9: number, v10: number, v11: number, v12: number, v13: number, v14: number, v15: number): {
    v0: number;
    v1: number;
    v2: number;
    v3: number;
    v4: number;
    v5: number;
    v6: number;
    v7: number;
    v8: number;
    v9: number;
    v10: number;
    v11: number;
    v12: number;
    v13: number;
    v14: number;
    v15: number;
};
declare class BLAKE2s extends BLAKE2<BLAKE2s> {
    private v0;
    private v1;
    private v2;
    private v3;
    private v4;
    private v5;
    private v6;
    private v7;
    constructor(opts?: BlakeOpts);
    protected get(): [number, number, number, number, number, number, number, number];
    protected set(v0: number, v1: number, v2: number, v3: number, v4: number, v5: number, v6: number, v7: number): void;
    protected compress(msg: Uint32Array, offset: number, isLast: boolean): void;
    destroy(): void;
}
/**
 * BLAKE2s - optimized for 32-bit platforms. JS doesn't have uint64, so it's faster than BLAKE2b.
 * @param msg - message that would be hashed
 * @param opts - dkLen, key, salt, personalization
 */
export declare const blake2s: {
    (msg: import("./utils.js").Input, opts?: BlakeOpts): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(opts: BlakeOpts): import("./utils.js").Hash<BLAKE2s>;
};
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/blake2s.d.ts`.

**Classes defined**: BLAKE2s

**Functions defined**: compress

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 47
- Comment lines: 5
- Blank lines: -4

### Main Components

**Functions** (1):
- `compress()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./_blake2.js` (imported)
- `./_blake2.js` (referenced)
- `./utils.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-hashes/blake2s.d.ts
```

