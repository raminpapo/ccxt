# Documentation: js/src/static_dependencies/noble-curves/_shortw_utils.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/_shortw_utils.d.ts`
- **Size**: 3,380 bytes
- **Lines**: 61
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { randomBytes } from '../noble-hashes/utils.js';
import { CurveType } from './abstract/weierstrass.js';
import { CHash } from './abstract/utils.js';
export declare function getHash(hash: CHash): {
    hash: CHash;
    hmac: (key: Uint8Array, ...msgs: Uint8Array[]) => Uint8Array;
    randomBytes: typeof randomBytes;
};
declare type CurveDef = Readonly<Omit<CurveType, 'hash' | 'hmac' | 'randomBytes'>>;
export declare function createCurve(curveDef: CurveDef, defHash: CHash): Readonly<{
    create: (hash: CHash) => import("./abstract/weierstrass.js").CurveFn;
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
        readonly isTorsionFree?: (c: import("./abstract/weierstrass.js").ProjConstructor<bigint>, point: import("./abstract/weierstrass.js").ProjPointType<bigint>) => boolean;
        readonly clearCofactor?: (c: import("./abstract/weierstrass.js").ProjConstructor<bigint>, point: import("./abstract/weierstrass.js").ProjPointType<bigint>) => import("./abstract/weierstrass.js").ProjPointType<bigint>;
        readonly hash: CHash;
        readonly hmac: (key: Uint8Array, ...messages: Uint8Array[]) => Uint8Array;
        readonly randomBytes: (bytesLength?: number) => Uint8Array;
        lowS: boolean;
        readonly bits2int?: (bytes: Uint8Array) => bigint;
        readonly bits2int_modN?: (bytes: Uint8Array) => bigint;
    }>;
    getPublicKey: (privateKey: import("./abstract/utils.js").PrivKey, isCompressed?: boolean) => Uint8Array;
    getSharedSecret: (privateA: import("./abstract/utils.js").PrivKey, publicB: import("./abstract/utils.js").Hex, isCompressed?: boolean) => Uint8Array;
    sign: (msgHash: import("./abstract/utils.js").Hex, privKey: import("./abstract/utils.js").PrivKey, opts?: import("./abstract/weierstrass.js").SignOpts) => import("./abstract/weierstrass.js").SignatureType;
    verify: (signature: import("./abstract/utils.js").Hex | {
        r: bigint;
        s: bigint;
    }, msgHash: import("./abstract/utils.js").Hex, publicKey: import("./abstract/utils.js").Hex, opts?: import("./abstract/weierstrass.js").VerOpts) => boolean;
    ProjectivePoint: import("./abstract/weierstrass.js").ProjConstructor<bigint>;
    Signature: import("./abstract/weierstrass.js").SignatureConstructor;
    utils: {
        normPrivateKeyToScalar: (key: import("./abstract/utils.js").PrivKey) => bigint;
        isValidPrivateKey(privateKey: import("./abstract/utils.js").PrivKey): boolean;
        randomPrivateKey: () => Uint8Array;
        precompute: (windowSize?: number, point?: import("./abstract/weierstrass.js").ProjPointType<bigint>) => import("./abstract/weierstrass.js").ProjPointType<bigint>;
    };
}>;
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-curves/_shortw_utils.d.ts`.

**Functions defined**: createCurve, getHash

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 60
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (2):
- `createCurve()`
- `getHash()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./abstract/weierstrass.js` (imported)
- `../noble-hashes/utils.js` (imported)
- `./abstract/utils.js` (imported)
- `./abstract/weierstrass.js` (referenced)
- `../noble-hashes/utils.js` (referenced)
- `./abstract/utils.js` (referenced)
- `./abstract/modular.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-curves/_shortw_utils.d.ts
```

