# Documentation: js/src/static_dependencies/noble-hashes/ripemd160.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/ripemd160.d.ts`
- **Size**: 743 bytes
- **Lines**: 25
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { SHA2 } from './_sha2.js';
export declare class RIPEMD160 extends SHA2<RIPEMD160> {
    private h0;
    private h1;
    private h2;
    private h3;
    private h4;
    constructor();
    protected get(): [number, number, number, number, number];
    protected set(h0: number, h1: number, h2: number, h3: number, h4: number): void;
    protected process(view: DataView, offset: number): void;
    protected roundClean(): void;
    destroy(): void;
}
/**
 * RIPEMD-160 - a hash function from 1990s.
 * @param message - msg that would be hashed
 */
export declare const ripemd160: {
    (message: import("./utils.js").Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): import("./utils.js").Hash<RIPEMD160>;
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/ripemd160.d.ts`.

**Classes defined**: RIPEMD160

**Functions defined**: from

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 24
- Comment lines: 4
- Blank lines: -3

### Main Components

**Functions** (1):
- `from()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./_sha2.js` (imported)
- `./_sha2.js` (referenced)
- `./utils.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-hashes/ripemd160.d.ts
```

