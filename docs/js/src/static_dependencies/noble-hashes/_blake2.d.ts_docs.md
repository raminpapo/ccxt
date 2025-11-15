# Documentation: js/src/static_dependencies/noble-hashes/_blake2.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/_blake2.d.ts`
- **Size**: 987 bytes
- **Lines**: 28
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Hash, Input } from './utils.js';
export declare const SIGMA: Uint8Array;
export declare type BlakeOpts = {
    dkLen?: number;
    key?: Input;
    salt?: Input;
    personalization?: Input;
};
export declare abstract class BLAKE2<T extends BLAKE2<T>> extends Hash<T> {
    readonly blockLen: number;
    outputLen: number;
    protected abstract compress(msg: Uint32Array, offset: number, isLast: boolean): void;
    protected abstract get(): number[];
    protected abstract set(...args: number[]): void;
    abstract destroy(): void;
    protected buffer: Uint8Array;
    protected buffer32: Uint32Array;
    protected length: number;
    protected pos: number;
    protected finished: boolean;
    protected destroyed: boolean;
    constructor(blockLen: number, outputLen: number, opts: BlakeOpts, keyLen: number, saltLen: number, persLen: number);
    update(data: Input): this;
    digestInto(out: Uint8Array): void;
    digest(): Uint8Array;
    _cloneInto(to?: T): T;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/_blake2.d.ts`.

**Classes defined**: BLAKE2

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 27
- Comment lines: 0
- Blank lines: 1

### Main Components



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
ts-node js/src/static_dependencies/noble-hashes/_blake2.d.ts
```

