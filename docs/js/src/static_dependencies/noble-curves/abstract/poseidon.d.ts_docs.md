# Documentation: js/src/static_dependencies/noble-curves/abstract/poseidon.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/abstract/poseidon.d.ts`
- **Size**: 878 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/*! noble-curves - MIT License (c) 2022 Paul Miller (paulmillr.com) */
import { Field } from './modular.js';
export declare type PoseidonOpts = {
    Fp: Field<bigint>;
    t: number;
    roundsFull: number;
    roundsPartial: number;
    sboxPower?: number;
    reversePartialPowIdx?: boolean;
    mds: bigint[][];
    roundConstants: bigint[][];
};
export declare function validateOpts(opts: PoseidonOpts): Readonly<{
    rounds: number;
    sboxFn: (n: bigint) => bigint;
    roundConstants: bigint[][];
    mds: bigint[][];
    Fp: Field<bigint>;
    t: number;
    roundsFull: number;
    roundsPartial: number;
    sboxPower?: number;
    reversePartialPowIdx?: boolean;
}>;
export declare function splitConstants(rc: bigint[], t: number): any[];
export declare function poseidon(opts: PoseidonOpts): {
    (values: bigint[]): bigint[];
    roundConstants: bigint[][];
};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-curves/abstract/poseidon.d.ts`.

**Functions defined**: splitConstants, validateOpts, poseidon

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 29
- Comment lines: 1
- Blank lines: 0

### Main Components

**Functions** (3):
- `poseidon()`
- `splitConstants()`
- `validateOpts()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./modular.js` (imported)
- `./modular.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-curves/abstract/poseidon.d.ts
```

