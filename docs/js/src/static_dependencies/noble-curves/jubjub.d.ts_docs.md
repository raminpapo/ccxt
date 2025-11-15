# Documentation: js/src/static_dependencies/noble-curves/jubjub.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/jubjub.d.ts`
- **Size**: 507 bytes
- **Lines**: 9
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * jubjub Twisted Edwards curve.
 * https://neuromancer.sk/std/other/JubJub
 * jubjub does not use EdDSA, so `hash`/sha512 params are passed because interface expects them.
 */
export declare const jubjub: import("./abstract/edwards.js").CurveFn;
export declare function groupHash(tag: Uint8Array, personalization: Uint8Array): import("./abstract/edwards.js").ExtPointType;
export declare function findGroupHash(m: Uint8Array, personalization: Uint8Array): import("./abstract/edwards.js").ExtPointType;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-curves/jubjub.d.ts`.

**Functions defined**: findGroupHash, groupHash

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 9
- Code lines: 8
- Comment lines: 5
- Blank lines: -4

### Main Components

**Functions** (2):
- `findGroupHash()`
- `groupHash()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./abstract/edwards.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-curves/jubjub.d.ts
```

