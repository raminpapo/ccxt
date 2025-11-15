# Documentation: js/src/static_dependencies/noble-hashes/sha3.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/sha3.d.ts`
- **Size**: 2,716 bytes
- **Lines**: 98
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Hash, Input, HashXOF } from './utils.js';
export declare function keccakP(s: Uint32Array, rounds?: number): void;
export declare class Keccak extends Hash<Keccak> implements HashXOF<Keccak> {
    blockLen: number;
    suffix: number;
    outputLen: number;
    protected enableXOF: boolean;
    protected rounds: number;
    protected state: Uint8Array;
    protected pos: number;
    protected posOut: number;
    protected finished: boolean;
    protected state32: Uint32Array;
    protected destroyed: boolean;
    constructor(blockLen: number, suffix: number, outputLen: number, enableXOF?: boolean, rounds?: number);
    protected keccak(): void;
    update(data: Input): this;
    protected finish(): void;
    protected writeInto(out: Uint8Array): Uint8Array;
    xofInto(out: Uint8Array): Uint8Array;
    xof(bytes: number): Uint8Array;
    digestInto(out: Uint8Array): Uint8Array;
    digest(): Uint8Array;
    destroy(): void;
    _cloneInto(to?: Keccak): Keccak;
}
export declare const sha3_224: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
/**
 * SHA3-256 hash function
 * @param message - that would be hashed
 */
export declare const sha3_256: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
export declare const sha3_384: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
export declare const sha3_512: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
export declare const keccak_224: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
/**
 * keccak-256 hash function. Different from SHA3-256.
 * @param message - that would be hashed
 */
export declare const keccak_256: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
export declare const keccak_384: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
export declare const keccak_512: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<Keccak>;
};
export declare type ShakeOpts = {
    dkLen?: number;
};
export declare const shake128: {
    (msg: Input, opts?: ShakeOpts): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(opts: ShakeOpts): Hash<Keccak>;
};
export declare const shake256: {
    (msg: Input, opts?: ShakeOpts): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(opts: ShakeOpts): Hash<Keccak>;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/sha3.d.ts`.

**Classes defined**: Keccak

**Functions defined**: keccakP

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 98
- Code lines: 97
- Comment lines: 8
- Blank lines: -7

### Main Components

**Functions** (1):
- `keccakP()`



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
ts-node js/src/static_dependencies/noble-hashes/sha3.d.ts
```

