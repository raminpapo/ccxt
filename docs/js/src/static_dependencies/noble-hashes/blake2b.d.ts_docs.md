# Documentation: js/src/static_dependencies/noble-hashes/blake2b.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/blake2b.d.ts`
- **Size**: 1,454 bytes
- **Lines**: 54
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BLAKE2, BlakeOpts } from './_blake2.js';
declare class BLAKE2b extends BLAKE2<BLAKE2b> {
    private v0l;
    private v0h;
    private v1l;
    private v1h;
    private v2l;
    private v2h;
    private v3l;
    private v3h;
    private v4l;
    private v4h;
    private v5l;
    private v5h;
    private v6l;
    private v6h;
    private v7l;
    private v7h;
    constructor(opts?: BlakeOpts);
    protected get(): [
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number,
        number
    ];
    protected set(v0l: number, v0h: number, v1l: number, v1h: number, v2l: number, v2h: number, v3l: number, v3h: number, v4l: number, v4h: number, v5l: number, v5h: number, v6l: number, v6h: number, v7l: number, v7h: number): void;
    protected compress(msg: Uint32Array, offset: number, isLast: boolean): void;
    destroy(): void;
}
/**
 * BLAKE2b - optimized for 64-bit platforms. JS doesn't have uint64, so it's slower than BLAKE2s.
 * @param msg - message that would be hashed
 * @param opts - dkLen, key, salt, personalization
 */
export declare const blake2b: {
    (msg: import("./utils.js").Input, opts?: BlakeOpts): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(opts: BlakeOpts): import("./utils.js").Hash<BLAKE2b>;
};
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/blake2b.d.ts`.

**Classes defined**: BLAKE2b

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 53
- Comment lines: 5
- Blank lines: -4

### Main Components



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
ts-node js/src/static_dependencies/noble-hashes/blake2b.d.ts
```

