# Documentation: ts/src/static_dependencies/noble-hashes/_assert.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/noble-hashes/_assert.ts`
- **Size**: 1,448 bytes
- **Lines**: 50
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export function number(n: number) {
  if (!Number.isSafeInteger(n) || n < 0) throw new Error(`Wrong positive integer: ${n}`);
}

export function bool(b: boolean) {
  if (typeof b !== 'boolean') throw new Error(`Expected boolean, not ${b}`);
}

export function bytes(b: Uint8Array | undefined, ...lengths: number[]) {
  if (!(b instanceof Uint8Array)) throw new TypeError('Expected Uint8Array');
  if (lengths.length > 0 && !lengths.includes(b.length))
    throw new TypeError(`Expected Uint8Array of length ${lengths}, not of length=${b.length}`);
}

type Hash = {
  (data: Uint8Array): Uint8Array;
  blockLen: number;
  outputLen: number;
  create: any;
};
export function hash(hash: Hash) {
  if (typeof hash !== 'function' || typeof hash.create !== 'function')
    throw new Error('Hash should be wrapped by utils.wrapConstructor');
  number(hash.outputLen);
  number(hash.blockLen);
}

export function exists(instance: any, checkFinished = true) {
  if (instance.destroyed) throw new Error('Hash instance has been destroyed');
  if (checkFinished && instance.finished) throw new Error('Hash#digest() has already been called');
}
export function output(out: any, instance: any) {
  bytes(out);
  const min = instance.outputLen;
  if (out.length < min) {
    throw new Error(`digestInto() expects output buffer of length at least ${min}`);
  }
}

const assert = {
  number,
  bool,
  bytes,
  hash,
  exists,
  output,
};

export default assert;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/noble-hashes/_assert.ts`.

**Functions defined**: hash, exists, bool, number, output, bytes



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 43
- Comment lines: 0
- Blank lines: 7

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
ts-node ts/src/static_dependencies/noble-hashes/_assert.ts
```

