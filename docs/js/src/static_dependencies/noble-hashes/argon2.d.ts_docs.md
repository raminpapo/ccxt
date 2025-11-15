# Documentation: js/src/static_dependencies/noble-hashes/argon2.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/argon2.d.ts`
- **Size**: 576 bytes
- **Lines**: 17
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Input } from './utils.js';
export declare type ArgonOpts = {
    t: number;
    m: number;
    p: number;
    version?: number;
    key?: Input;
    personalization?: Input;
    dkLen?: number;
    asyncTick?: number;
    maxmem?: number;
    onProgress?: (progress: number) => void;
};
export declare const argon2d: (password: Input, salt: Input, opts: ArgonOpts) => Uint8Array;
export declare const argon2i: (password: Input, salt: Input, opts: ArgonOpts) => Uint8Array;
export declare const argon2id: (password: Input, salt: Input, opts: ArgonOpts) => Uint8Array;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/argon2.d.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 16
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
ts-node js/src/static_dependencies/noble-hashes/argon2.d.ts
```

