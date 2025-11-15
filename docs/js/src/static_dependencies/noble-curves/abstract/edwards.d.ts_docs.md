# Documentation: js/src/static_dependencies/noble-curves/abstract/edwards.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/abstract/edwards.d.ts`
- **Size**: 2,931 bytes
- **Lines**: 80
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import * as ut from './utils.js';
import { FHash, Hex } from './utils.js';
import { Group, GroupConstructor, BasicCurve, AffinePoint } from './curve.js';
export declare type CurveType = BasicCurve<bigint> & {
    a: bigint;
    d: bigint;
    hash: FHash;
    randomBytes: (bytesLength?: number) => Uint8Array;
    adjustScalarBytes?: (bytes: Uint8Array) => Uint8Array;
    domain?: (data: Uint8Array, ctx: Uint8Array, phflag: boolean) => Uint8Array;
    uvRatio?: (u: bigint, v: bigint) => {
        isValid: boolean;
        value: bigint;
    };
    preHash?: FHash;
    mapToCurve?: (scalar: bigint[]) => AffinePoint<bigint>;
};
declare function validateOpts(curve: CurveType): Readonly<{
    readonly nBitLength: number;
    readonly nByteLength: number;
    readonly Fp: import("./modular.js").Field<bigint>;
    readonly n: bigint;
    readonly h: bigint;
    readonly hEff?: bigint;
    readonly Gx: bigint;
    readonly Gy: bigint;
    readonly allowInfinityPoint?: boolean;
    readonly a: bigint;
    readonly d: bigint;
    readonly hash: ut.FHash;
    readonly randomBytes: (bytesLength?: number) => Uint8Array;
    readonly adjustScalarBytes?: (bytes: Uint8Array) => Uint8Array;
    readonly domain?: (data: Uint8Array, ctx: Uint8Array, phflag: boolean) => Uint8Array;
    readonly uvRatio?: (u: bigint, v: bigint) => {
        isValid: boolean;
        value: bigint;
    };
    readonly preHash?: ut.FHash;
    readonly mapToCurve?: (scalar: bigint[]) => AffinePoint<bigint>;
}>;
export interface ExtPointType extends Group<ExtPointType> {
    readonly ex: bigint;
    readonly ey: bigint;
    readonly ez: bigint;
    readonly et: bigint;
    assertValidity(): void;
    multiply(scalar: bigint): ExtPointType;
    multiplyUnsafe(scalar: bigint): ExtPointType;
    isSmallOrder(): boolean;
    isTorsionFree(): boolean;
    clearCofactor(): ExtPointType;
    toAffine(iz?: bigint): AffinePoint<bigint>;
}
export interface ExtPointConstructor extends GroupConstructor<ExtPointType> {
    new (x: bigint, y: bigint, z: bigint, t: bigint): ExtPointType;
    fromAffine(p: AffinePoint<bigint>): ExtPointType;
    fromHex(hex: Hex): ExtPointType;
    fromPrivateKey(privateKey: Hex): ExtPointType;
}
export declare type CurveFn = {
    CURVE: ReturnType<typeof validateOpts>;
    getPublicKey: (privateKey: Hex) => Uint8Array;
    sign: (message: Hex, privateKey: Hex) => Uint8Array;
    signModified?: (message: Hex, privateKey: Hex) => Uint8Array;
    verify: (sig: Hex, message: Hex, publicKey: Hex) => boolean;
    ExtendedPoint: ExtPointConstructor;
    utils: {
        randomPrivateKey: () => Uint8Array;
        getExtendedPublicKey: (key: Hex) => {
            head: Uint8Array;
            prefix: Uint8Array;
            scalar: bigint;
            point: ExtPointType;
            pointBytes: Uint8Array;
        };
    };
};
export declare function twistedEdwards(curveDef: CurveType): CurveFn;
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-curves/abstract/edwards.d.ts`.

**Functions defined**: validateOpts, twistedEdwards

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 79
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `twistedEdwards()`
- `validateOpts()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./utils.js` (imported)
- `./curve.js` (imported)
- `./modular.js` (referenced)
- `./utils.js` (referenced)
- `./curve.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-curves/abstract/edwards.d.ts
```

