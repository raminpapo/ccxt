# Documentation: js/src/static_dependencies/noble-hashes/_assert.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/_assert.d.ts`
- **Size**: 697 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare function number(n: number): void;
export declare function bool(b: boolean): void;
export declare function bytes(b: Uint8Array | undefined, ...lengths: number[]): void;
declare type Hash = {
    (data: Uint8Array): Uint8Array;
    blockLen: number;
    outputLen: number;
    create: any;
};
export declare function hash(hash: Hash): void;
export declare function exists(instance: any, checkFinished?: boolean): void;
export declare function output(out: any, instance: any): void;
declare const assert: {
    number: typeof number;
    bool: typeof bool;
    bytes: typeof bytes;
    hash: typeof hash;
    exists: typeof exists;
    output: typeof output;
};
export default assert;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-hashes/_assert.d.ts`.

**Functions defined**: hash, exists, bool, number, output, bytes



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 21
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (6):
- `bool()`
- `bytes()`
- `exists()`
- `hash()`
- `number()`
- `output()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-hashes/_assert.d.ts
```

