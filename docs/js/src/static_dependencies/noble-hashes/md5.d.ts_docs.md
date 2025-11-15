# Documentation: js/src/static_dependencies/noble-hashes/md5.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/md5.d.ts`
- **Size**: 464 bytes
- **Lines**: 19
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Hash, Input } from './utils.js';
declare class MD5 extends Hash<MD5> {
    blockLen: number;
    outputLen: number;
    protected _buffer: Uint8Array;
    digest(): Uint8Array;
    digestInto(buf: Uint8Array): void;
    _cloneInto(to: MD5 | undefined): MD5;
    destroy(): void;
    update(buf: Input): this;
}
export declare let md5: {
    (message: Input): Uint8Array;
    outputLen: number;
    blockLen: number;
    create(): Hash<MD5>;
};
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/md5.d.ts`.

**Classes defined**: MD5

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 18
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
ts-node js/src/static_dependencies/noble-hashes/md5.d.ts
```

