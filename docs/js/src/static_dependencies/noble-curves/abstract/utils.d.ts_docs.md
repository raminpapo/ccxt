# Documentation: js/src/static_dependencies/noble-curves/abstract/utils.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/noble-curves/abstract/utils.d.ts`
- **Size**: 2,743 bytes
- **Lines**: 54
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare type Hex = Uint8Array | string;
export declare type PrivKey = Hex | bigint;
export declare type CHash = {
    (message: Uint8Array | string): Uint8Array;
    blockLen: number;
    outputLen: number;
    create(opts?: {
        dkLen?: number;
    }): any;
};
export declare type FHash = (message: Uint8Array | string) => Uint8Array;
export declare function bytesToHex(bytes: Uint8Array): string;
export declare function numberToHexUnpadded(num: number | bigint): string;
export declare function hexToNumber(hex: string): bigint;
export declare function hexToBytes(hex: string): Uint8Array;
export declare function bytesToNumberBE(bytes: Uint8Array): bigint;
export declare function bytesToNumberLE(bytes: Uint8Array): bigint;
export declare const numberToBytesBE: (n: bigint, len: number) => Uint8Array;
export declare const numberToBytesLE: (n: bigint, len: number) => Uint8Array;
export declare const numberToVarBytesBE: (n: bigint) => Uint8Array;
export declare function ensureBytes(title: string, hex: Hex, expectedLength?: number): Uint8Array;
export declare function concatBytes(...arrs: Uint8Array[]): Uint8Array;
export declare function equalBytes(b1: Uint8Array, b2: Uint8Array): boolean;
export declare function utf8ToBytes(str: string): Uint8Array;
export declare function bitLen(n: bigint): any;
export declare const bitGet: (n: bigint, pos: number) => bigint;
export declare const bitSet: (n: bigint, pos: number, value: boolean) => bigint;
export declare const bitMask: (n: number) => bigint;
declare type Pred<T> = (v: Uint8Array) => T | undefined;
/**
 * Minimal HMAC-DRBG from NIST 800-90 for RFC6979 sigs.
 * @returns function that will call DRBG until 2nd arg returns something meaningful
 * @example
 *   const drbg = createHmacDRBG<Key>(32, 32, hmac);
 *   drbg(seed, bytesToKey); // bytesToKey must return Key or undefined
 */
export declare function createHmacDrbg<T>(hashLen: number, qByteLen: number, hmacFn: (key: Uint8Array, ...messages: Uint8Array[]) => Uint8Array): (seed: Uint8Array, predicate: Pred<T>) => T;
declare const validatorFns: {
    readonly bigint: (val: any) => boolean;
    readonly function: (val: any) => boolean;
    readonly boolean: (val: any) => boolean;
    readonly string: (val: any) => boolean;
    readonly isSafeInteger: (val: any) => boolean;
    readonly array: (val: any) => boolean;
    readonly field: (val: any, object: any) => any;
    readonly hash: (val: any) => boolean;
};
declare type Validator = keyof typeof validatorFns;
declare type ValMap<T extends Record<string, any>> = {
    [K in keyof T]?: Validator;
};
export declare function validateObject<T extends Record<string, any>>(object: T, validators: ValMap<T>, optValidators?: ValMap<T>): T;
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/noble-curves/abstract/utils.d.ts`.

**Functions defined**: bytesToHex, numberToHexUnpadded, concatBytes, ensureBytes, bytesToNumberBE, hexToBytes, equalBytes, hexToNumber, bytesToNumberLE, utf8ToBytes

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 53
- Comment lines: 7
- Blank lines: -6

### Main Components

**Functions** (14):
- `bitLen()`
- `bytesToHex()`
- `bytesToNumberBE()`
- `bytesToNumberLE()`
- `concatBytes()`
- `createHmacDrbg()`
- `ensureBytes()`
- `equalBytes()`
- `hexToBytes()`
- `hexToNumber()`
- `numberToHexUnpadded()`
- `that()`
- `utf8ToBytes()`
- `validateObject()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/noble-curves/abstract/utils.d.ts
```

