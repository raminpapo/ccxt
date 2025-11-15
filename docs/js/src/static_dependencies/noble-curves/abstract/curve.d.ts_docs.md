# Documentation: js/src/static_dependencies/noble-curves/abstract/curve.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/abstract/curve.d.ts`
- **Size**: 2,210 bytes
- **Lines**: 68
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/*! noble-curves - MIT License (c) 2022 Paul Miller (paulmillr.com) */
import { Field } from './modular.js';
export declare type AffinePoint<T> = {
    x: T;
    y: T;
} & {
    z?: never;
    t?: never;
};
export interface Group<T extends Group<T>> {
    double(): T;
    negate(): T;
    add(other: T): T;
    subtract(other: T): T;
    equals(other: T): boolean;
    multiply(scalar: bigint): T;
}
export declare type GroupConstructor<T> = {
    BASE: T;
    ZERO: T;
};
export declare type Mapper<T> = (i: T[]) => T[];
export declare function wNAF<T extends Group<T>>(c: GroupConstructor<T>, bits: number): {
    constTimeNegate: (condition: boolean, item: T) => T;
    unsafeLadder(elm: T, n: bigint): T;
    /**
     * Creates a wNAF precomputation window. Used for caching.
     * Default window size is set by `utils.precompute()` and is equal to 8.
     * Number of precomputed points depends on the curve size:
     * 2^(𝑊−1) * (Math.ceil(𝑛 / 𝑊) + 1), where:
     * - 𝑊 is the window size
     * - 𝑛 is the bitlength of the curve order.
     * For a 256-bit curve and window size 8, the number of precomputed points is 128 * 33 = 4224.
     * @returns precomputed point tables flattened to a single array
     */
    precomputeWindow(elm: T, W: number): Group<T>[];
    /**
     * Implements ec multiplication using precomputed tables and w-ary non-adjacent form.
     * @param W window size
     * @param precomputes precomputed tables
     * @param n scalar (we don't check here, but should be less than curve order)
     * @returns real and fake (for const-time) points
     */
    wNAF(W: number, precomputes: T[], n: bigint): {
        p: T;
        f: T;
    };
    wNAFCached(P: T, precomputesMap: Map<T, T[]>, n: bigint, transform: Mapper<T>): {
        p: T;
        f: T;
    };
};
export declare type BasicCurve<T> = {
    Fp: Field<T>;
    n: bigint;
    nBitLength?: number;
    nByteLength?: number;
    h: bigint;
    hEff?: bigint;
    Gx: T;
    Gy: T;
    allowInfinityPoint?: boolean;
};
export declare function validateBasic<FP, T>(curve: BasicCurve<FP> & T): Readonly<{
    readonly nBitLength: number;
    readonly nByteLength: number;
} & BasicCurve<FP> & T>;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-curves/abstract/curve.d.ts`.

**Functions defined**: wNAF, validateBasic

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 68
- Code lines: 67
- Comment lines: 18
- Blank lines: -17

### Main Components

**Functions** (2):
- `validateBasic()`
- `wNAF()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `./modular.js` (imported)
- `./modular.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-curves/abstract/curve.d.ts
```

