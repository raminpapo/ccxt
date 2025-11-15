# Documentation: js/src/static_dependencies/scure-starknet/index.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/scure-starknet/index.d.ts`
- **Size**: 4,287 bytes
- **Lines**: 80
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Field } from '../noble-curves/abstract/modular.js';
import { poseidon } from '../noble-curves/abstract/poseidon.js';
import { ProjPointType, SignatureType } from '../noble-curves/abstract/weierstrass.js';
import * as u from '../noble-curves/abstract/utils.js';
import type { Hex } from '../noble-curves/abstract/utils';
declare type ProjectivePoint = ProjPointType<bigint>;
export declare const MAX_VALUE: bigint;
export declare const _starkCurve: import("../noble-curves/abstract/weierstrass.js").CurveFn;
export declare function getPublicKey(privKey: Hex, isCompressed?: boolean): Uint8Array;
export declare function getSharedSecret(privKeyA: Hex, pubKeyB: Hex): Uint8Array;
export declare function sign(msgHash: Hex, privKey: Hex, opts?: any): SignatureType;
export declare function verify(signature: SignatureType | Hex, msgHash: Hex, pubKey: Hex): boolean;
declare const CURVE: Readonly<{
    readonly nBitLength: number;
    readonly nByteLength: number;
    readonly Fp: Field<bigint>;
    readonly n: bigint;
    readonly h: bigint;
    readonly hEff?: bigint;
    readonly Gx: bigint;
    readonly Gy: bigint;
    readonly allowInfinityPoint?: boolean;
    readonly a: bigint;
    readonly b: bigint;
    readonly allowedPrivateKeyLengths?: readonly number[];
    readonly wrapPrivateKey?: boolean;
    readonly endo?: {
        beta: bigint;
        splitScalar: (k: bigint) => {
            k1neg: boolean;
            k1: bigint;
            k2neg: boolean;
            k2: bigint;
        };
    };
    readonly isTorsionFree?: (c: import("../noble-curves/abstract/weierstrass.js").ProjConstructor<bigint>, point: ProjPointType<bigint>) => boolean;
    readonly clearCofactor?: (c: import("../noble-curves/abstract/weierstrass.js").ProjConstructor<bigint>, point: ProjPointType<bigint>) => ProjPointType<bigint>;
    readonly hash: u.CHash;
    readonly hmac: (key: Uint8Array, ...messages: Uint8Array[]) => Uint8Array;
    readonly randomBytes: (bytesLength?: number) => Uint8Array;
    lowS: boolean;
    readonly bits2int?: (bytes: Uint8Array) => bigint;
    readonly bits2int_modN?: (bytes: Uint8Array) => bigint;
}>, ProjectivePoint: import("../noble-curves/abstract/weierstrass.js").ProjConstructor<bigint>, Signature: import("../noble-curves/abstract/weierstrass.js").SignatureConstructor, utils: {
    normPrivateKeyToScalar: (key: u.PrivKey) => bigint;
    isValidPrivateKey(privateKey: u.PrivKey): boolean;
    randomPrivateKey: () => Uint8Array;
    precompute: (windowSize?: number, point?: ProjPointType<bigint>) => ProjPointType<bigint>;
};
export { CURVE, ProjectivePoint, Signature, utils };
export declare function grindKey(seed: Hex): string;
export declare function getStarkKey(privateKey: Hex): string;
export declare function ethSigToPrivate(signature: string): string;
export declare function getAccountPath(layer: string, application: string, ethereumAddress: string, index: number): string;
declare type PedersenArg = Hex | bigint | number;
export declare function pedersen(x: PedersenArg, y: PedersenArg): string;
export declare const computeHashOnElements: (data: PedersenArg[], fn?: typeof pedersen) => PedersenArg;
export declare const keccak: (data: Uint8Array) => bigint;
export declare const Fp251: Readonly<Field<bigint> & Required<Pick<Field<bigint>, "isOdd">>>;
export declare function _poseidonMDS(Fp: Field<bigint>, name: string, m: number, attempt?: number): bigint[][];
export declare type PoseidonOpts = {
    Fp: Field<bigint>;
    rate: number;
    capacity: number;
    roundsFull: number;
    roundsPartial: number;
};
export declare type PoseidonFn = ReturnType<typeof poseidon> & {
    m: number;
    rate: number;
    capacity: number;
};
export declare function poseidonBasic(opts: PoseidonOpts, mds: bigint[][]): PoseidonFn;
export declare function poseidonCreate(opts: PoseidonOpts, mdsAttempt?: number): PoseidonFn;
export declare const poseidonSmall: PoseidonFn;
export declare function poseidonHash(x: bigint, y: bigint, fn?: PoseidonFn): bigint;
export declare function poseidonHashFunc(x: Uint8Array, y: Uint8Array, fn?: PoseidonFn): Uint8Array;
export declare function poseidonHashSingle(x: bigint, fn?: PoseidonFn): bigint;
export declare function poseidonHashMany(values: bigint[], fn?: PoseidonFn): bigint;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/scure-starknet/index.d.ts`.

**Functions defined**: _poseidonMDS, getSharedSecret, verify, sign, getPublicKey, pedersen, grindKey, getStarkKey, getAccountPath, ethSigToPrivate

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 79
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (16):
- `_poseidonMDS()`
- `ethSigToPrivate()`
- `getAccountPath()`
- `getPublicKey()`
- `getSharedSecret()`
- `getStarkKey()`
- `grindKey()`
- `pedersen()`
- `poseidonBasic()`
- `poseidonCreate()`
- `poseidonHash()`
- `poseidonHashFunc()`
- `poseidonHashMany()`
- `poseidonHashSingle()`
- `sign()`
- `verify()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../noble-curves/abstract/utils.js` (imported)
- `../noble-curves/abstract/modular.js` (imported)
- `../noble-curves/abstract/utils` (imported)
- `../noble-curves/abstract/weierstrass.js` (imported)
- `../noble-curves/abstract/poseidon.js` (imported)
- `../noble-curves/abstract/poseidon.js` (referenced)
- `../noble-curves/abstract/weierstrass.js` (referenced)
- `../noble-curves/abstract/utils.js` (referenced)
- `../noble-curves/abstract/modular.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/scure-starknet/index.d.ts
```

