# Documentation: js/src/static_dependencies/noble-hashes/_sha2.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/_sha2.d.ts`
- **Size**: 864 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Hash, Input } from './utils.js';
export declare abstract class SHA2<T extends SHA2<T>> extends Hash<T> {
    readonly blockLen: number;
    outputLen: number;
    readonly padOffset: number;
    readonly isLE: boolean;
    protected abstract process(buf: DataView, offset: number): void;
    protected abstract get(): number[];
    protected abstract set(...args: number[]): void;
    abstract destroy(): void;
    protected abstract roundClean(): void;
    protected buffer: Uint8Array;
    protected view: DataView;
    protected finished: boolean;
    protected length: number;
    protected pos: number;
    protected destroyed: boolean;
    constructor(blockLen: number, outputLen: number, padOffset: number, isLE: boolean);
    update(data: Input): this;
    digestInto(out: Uint8Array): void;
    digest(): Uint8Array;
    _cloneInto(to?: T): T;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/_sha2.d.ts`.

**Classes defined**: SHA2

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 23
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
ts-node js/src/static_dependencies/noble-hashes/_sha2.d.ts
```

