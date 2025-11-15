# Documentation: js/src/static_dependencies/noble-curves/secp256k1.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/secp256k1.d.ts`
- **Size**: 4,356 bytes
- **Lines**: 92
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { mod } from './abstract/modular.js';
import { ProjPointType as PointType } from './abstract/weierstrass.js';
import type { Hex, PrivKey } from './abstract/utils.js';
import { bytesToNumberBE } from './abstract/utils.js';
import * as htf from './abstract/hash-to-curve.js';
export declare const secp256k1: Readonly<{
    create: (hash: import("./abstract/utils.js").CHash) => import("./abstract/weierstrass.js").CurveFn;
    CURVE: Readonly<{
        readonly nBitLength: number;
        readonly nByteLength: number;
        readonly Fp: import("./abstract/modular.js").Field<bigint>;
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
        readonly isTorsionFree?: (c: import("./abstract/weierstrass.js").ProjConstructor<bigint>, point: PointType<bigint>) => boolean;
        readonly clearCofactor?: (c: import("./abstract/weierstrass.js").ProjConstructor<bigint>, point: PointType<bigint>) => PointType<bigint>;
        readonly hash: import("./abstract/utils.js").CHash;
        readonly hmac: (key: Uint8Array, ...messages: Uint8Array[]) => Uint8Array;
        readonly randomBytes: (bytesLength?: number) => Uint8Array;
        lowS: boolean;
        readonly bits2int?: (bytes: Uint8Array) => bigint;
        readonly bits2int_modN?: (bytes: Uint8Array) => bigint;
    }>;
    getPublicKey: (privateKey: PrivKey, isCompressed?: boolean) => Uint8Array;
    getSharedSecret: (privateA: PrivKey, publicB: Hex, isCompressed?: boolean) => Uint8Array;
    sign: (msgHash: Hex, privKey: PrivKey, opts?: import("./abstract/weierstrass.js").SignOpts) => import("./abstract/weierstrass.js").SignatureType;
    verify: (signature: Hex | {
        r: bigint;
        s: bigint;
    }, msgHash: Hex, publicKey: Hex, opts?: import("./abstract/weierstrass.js").VerOpts) => boolean;
    ProjectivePoint: import("./abstract/weierstrass.js").ProjConstructor<bigint>;
    Signature: import("./abstract/weierstrass.js").SignatureConstructor;
    utils: {
        normPrivateKeyToScalar: (key: PrivKey) => bigint;
        isValidPrivateKey(privateKey: PrivKey): boolean;
        randomPrivateKey: () => Uint8Array;
        precompute: (windowSize?: number, point?: PointType<bigint>) => PointType<bigint>;
    };
}>;
declare function taggedHash(tag: string, ...messages: Uint8Array[]): Uint8Array;
/**
 * lift_x from BIP340. Convert 32-byte x coordinate to elliptic curve point.
 * @returns valid point checked for being on-curve
 */
declare function lift_x(x: bigint): PointType<bigint>;
/**
 * Schnorr public key is just `x` coordinate of Point as per BIP340.
 */
declare function schnorrGetPublicKey(privateKey: Hex): Uint8Array;
/**
 * Creates Schnorr signature as per BIP340. Verifies itself before returning anything.
 * auxRand is optional and is not the sole source of k generation: bad CSPRNG won't be dangerous.
 */
declare function schnorrSign(message: Hex, privateKey: PrivKey, auxRand?: Hex): Uint8Array;
/**
 * Verifies Schnorr signature.
 * Will swallow errors & return false except for initial type validation of arguments.
 */
declare function schnorrVerify(signature: Hex, message: Hex, publicKey: Hex): boolean;
export declare const schnorr: {
    getPublicKey: typeof schnorrGetPublicKey;
    sign: typeof schnorrSign;
    verify: typeof schnorrVerify;
    utils: {
        randomPrivateKey: () => Uint8Array;
        lift_x: typeof lift_x;
        pointToBytes: (point: PointType<bigint>) => Uint8Array;
        numberToBytesBE: (n: bigint, len: number) => Uint8Array;
        bytesToNumberBE: typeof bytesToNumberBE;
        taggedHash: typeof taggedHash;
        mod: typeof mod;
    };
};
export declare const hashToCurve: (msg: Uint8Array, options?: htf.htfBasicOpts) => htf.H2CPoint<bigint>, encodeToCurve: (msg: Uint8Array, options?: htf.htfBasicOpts) => htf.H2CPoint<bigint>;
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-curves/secp256k1.d.ts`.

**Functions defined**: schnorrGetPublicKey, lift_x, taggedHash, schnorrSign, schnorrVerify

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 92
- Code lines: 91
- Comment lines: 15
- Blank lines: -14

### Main Components

**Functions** (5):
- `lift_x()`
- `schnorrGetPublicKey()`
- `schnorrSign()`
- `schnorrVerify()`
- `taggedHash()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./abstract/hash-to-curve.js` (imported)
- `./abstract/weierstrass.js` (imported)
- `./abstract/utils.js` (imported)
- `./abstract/modular.js` (imported)
- `./abstract/hash-to-curve.js` (referenced)
- `./abstract/weierstrass.js` (referenced)
- `./abstract/utils.js` (referenced)
- `./abstract/modular.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-curves/secp256k1.d.ts
```

