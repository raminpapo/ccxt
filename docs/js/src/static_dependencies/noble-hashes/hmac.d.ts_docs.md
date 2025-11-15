# Documentation: js/src/static_dependencies/noble-hashes/hmac.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/hmac.d.ts`
- **Size**: 751 bytes
- **Lines**: 27
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Hash, CHash, Input } from './utils.js';
declare class HMAC<T extends Hash<T>> extends Hash<HMAC<T>> {
    oHash: T;
    iHash: T;
    blockLen: number;
    outputLen: number;
    private finished;
    private destroyed;
    constructor(hash: CHash, _key: Input);
    update(buf: Input): this;
    digestInto(out: Uint8Array): void;
    digest(): Uint8Array;
    _cloneInto(to?: HMAC<T>): HMAC<T>;
    destroy(): void;
}
/**
 * HMAC: RFC2104 message authentication code.
 * @param hash - function that would be used e.g. sha256
 * @param key - message key
 * @param message - message data
 */
export declare const hmac: {
    (hash: CHash, key: Input, message: Input): Uint8Array;
    create(hash: CHash, key: Input): HMAC<any>;
};
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/hmac.d.ts`.

**Classes defined**: HMAC

**Functions defined**: that

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 26
- Comment lines: 6
- Blank lines: -5

### Main Components

**Functions** (1):
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
ts-node js/src/static_dependencies/noble-hashes/hmac.d.ts
```

