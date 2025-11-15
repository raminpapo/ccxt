# Documentation: js/src/static_dependencies/noble-hashes/blake3.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/blake3.d.ts`
- **Size**: 1,307 bytes
- **Lines**: 47
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BLAKE2 } from './_blake2.js';
import { Input, HashXOF } from './utils.js';
export declare type Blake3Opts = {
    dkLen?: number;
    key?: Input;
    context?: Input;
};
declare class BLAKE3 extends BLAKE2<BLAKE3> implements HashXOF<BLAKE3> {
    private IV;
    private flags;
    private state;
    private chunkPos;
    private chunksDone;
    private stack;
    private posOut;
    private bufferOut32;
    private bufferOut;
    private chunkOut;
    private enableXOF;
    constructor(opts?: Blake3Opts, flags?: number);
    protected get(): any[];
    protected set(): void;
    private b2Compress;
    protected compress(buf: Uint32Array, bufPos?: number, isLast?: boolean): void;
    _cloneInto(to?: BLAKE3): BLAKE3;
    destroy(): void;
    private b2CompressOut;
    protected finish(): void;
    private writeInto;
    xofInto(out: Uint8Array): Uint8Array;
    xof(bytes: number): Uint8Array;
    digestInto(out: Uint8Array): Uint8Array;
    digest(): Uint8Array;
}
/**
 * BLAKE3 hash function.
 * @param msg - message that would be hashed
 * @param opts - dkLen, key, context
 */
export declare const blake3: {
    (msg: Input, opts?: Blake3Opts): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(opts: Blake3Opts): import("./utils.js").Hash<BLAKE3>;
};
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/blake3.d.ts`.

**Classes defined**: BLAKE3

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 46
- Comment lines: 5
- Blank lines: -4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./_blake2.js` (imported)
- `./utils.js` (imported)
- `./_blake2.js` (referenced)
- `./utils.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-hashes/blake3.d.ts
```

