# Documentation: js/src/static_dependencies/ethers/utils/maths.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/maths.d.ts`
- **Size**: 2,441 bytes
- **Lines**: 66
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import type { BytesLike } from "./data.js";
/**
 *  Any type that can be used where a numeric value is needed.
 */
export declare type Numeric = number | bigint;
/**
 *  Any type that can be used where a big number is needed.
 */
export declare type BigNumberish = string | Numeric;
/**
 *  Convert %%value%% from a twos-compliment representation of %%width%%
 *  bits to its value.
 *
 *  If the highest bit is ``1``, the result will be negative.
 */
export declare function fromTwos(_value: BigNumberish, _width: Numeric): bigint;
/**
 *  Convert %%value%% to a twos-compliment representation of
 *  %%width%% bits.
 *
 *  The result will always be positive.
 */
export declare function toTwos(_value: BigNumberish, _width: Numeric): bigint;
/**
 *  Mask %%value%% with a bitmask of %%bits%% ones.
 */
export declare function mask(_value: BigNumberish, _bits: Numeric): bigint;
/**
 *  Gets a BigInt from %%value%%. If it is an invalid value for
 *  a BigInt, then an ArgumentError will be thrown for %%name%%.
 */
export declare function getBigInt(value: BigNumberish, name?: string): bigint;
/**
 *  Returns %%value%% as a bigint, validating it is valid as a bigint
 *  value and that it is positive.
 */
export declare function getUint(value: BigNumberish, name?: string): bigint;
export declare function toBigInt(value: BigNumberish | Uint8Array): bigint;
/**
 *  Gets a //number// from %%value%%. If it is an invalid value for
 *  a //number//, then an ArgumentError will be thrown for %%name%%.
 */
export declare function getNumber(value: BigNumberish, name?: string): number;
/**
 *  Converts %%value%% to a number. If %%value%% is a Uint8Array, it
 *  is treated as Big Endian data. Throws if the value is not safe.
 */
export declare function toNumber(value: BigNumberish | Uint8Array): number;
/**
 *  Converts %%value%% to a Big Endian hexstring, optionally padded to
 *  %%width%% bytes.
 */
export declare function toBeHex(_value: BigNumberish, _width?: Numeric): string;
/**
 *  Converts %%value%% to a Big Endian Uint8Array.
 */
export declare function toBeArray(_value: BigNumberish): Uint8Array;
/**
 *  Returns a [[HexString]] for %%value%% safe to use as a //Quantity//.
 *
 *  A //Quantity// does not have and leading 0 values unless the value is
 *  the literal value `0x0`. This is most commonly used for JSSON-RPC
 *  numeric values.
 */
export declare function toQuantity(value: BytesLike | BigNumberish): string;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/utils/maths.d.ts`.

**Functions defined**: getUint, toBigInt, toNumber, fromTwos, getBigInt, toBeArray, toBeHex, mask, toTwos, getNumber

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 65
- Comment lines: 51
- Blank lines: -50

### Main Components

**Functions** (11):
- `fromTwos()`
- `getBigInt()`
- `getNumber()`
- `getUint()`
- `mask()`
- `toBeArray()`
- `toBeHex()`
- `toBigInt()`
- `toNumber()`
- `toQuantity()`
- `toTwos()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./data.js` (imported)
- `./data.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/utils/maths.d.ts
```

