# Documentation: ts/src/static_dependencies/starknet/utils/selector.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/selector.ts`
- **Size**: 2,790 bytes
- **Lines**: 86
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { keccak } from '../../scure-starknet/index.js';
import { MASK_250 } from '../constants.js';
import { BigNumberish } from '../types/index.js';
import { addHexPrefix, removeHexPrefix, utf8ToArray } from './encode.js';
import { hexToBytes, isHex, isStringWholeNumber, toHex, toHexString } from './num.js';

/**
 * Calculate hex-string keccak hash for a given BigNumberish
 *
 * BigNumberish -> hex-string keccak hash
 * @returns format: hex-string
 */
export function keccakBn(value: BigNumberish): string {
  const hexWithoutPrefix = removeHexPrefix(toHex(BigInt(value)));
  const evenHex = hexWithoutPrefix.length % 2 === 0 ? hexWithoutPrefix : `0${hexWithoutPrefix}`;
  return addHexPrefix(keccak(hexToBytes(addHexPrefix(evenHex))).toString(16));
}

/**
 * Calculate hex-string keccak hash for a given string
 *
 * String -> hex-string keccak hash
 * @returns format: hex-string
 */
function keccakHex(str: string): string {
  return addHexPrefix(keccak(utf8ToArray(str)).toString(16));
}

/**
 * Calculate bigint keccak hash for a given string
 *
 * String -> bigint keccak hash
 *
 * [Reference](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/public/abi.py#L17-L22)
 * @param str the value you want to get the keccak hash from
 * @returns starknet keccak hash as BigInt
 */
export function starknetKeccak(str: string): bigint {
  const hash = BigInt(keccakHex(str));
  // eslint-disable-next-line no-bitwise
  return hash & MASK_250;
}

/**
 * Calculate hex-string selector for a given abi-function-name
 *
 * Abi-function-name -> hex-string selector
 *
 * [Reference](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/public/abi.py#L25-L26)
 * @param funcName ascii-string of 'abi function name'
 * @returns format: hex-string; selector for 'abi function name'
 */
export function getSelectorFromName(funcName: string) {
  // sometimes BigInteger pads the hex string with zeros, which is not allowed in the starknet api
  return toHex(starknetKeccak(funcName));
}

/**
 * Calculate hex-string selector from abi-function-name, decimal string or hex string
 *
 * ('abi-function-name' or dec-string or hex-string) -> hex-string selector
 *
 * @param value hex-string | dec-string | ascii-string
 * @returns format: hex-string
 * @example
 * ```typescript
 * const selector: string = getSelector("myFunction");
 * // selector = "0x7e44bafo"
 *
 * const selector1: string = getSelector("0x123abc");
 * // selector1 = "0x123abc"
 *
 * const selector2: string = getSelector("123456");
 * // selector2 = "0x1e240"
 * ```
 */
export function getSelector(value: string) {
  if (isHex(value)) {
    return value;
  }
  if (isStringWholeNumber(value)) {
    return toHexString(value);
  }
  return getSelectorFromName(value);
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/selector.ts`.

**Functions defined**: keccakHex, getSelector, keccakBn, getSelectorFromName, starknetKeccak, name

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 86
- Code lines: 78
- Comment lines: 51
- Blank lines: -43

### Main Components

**Functions** (6):
- `getSelector()`
- `getSelectorFromName()`
- `keccakBn()`
- `keccakHex()`
- `name()`
- `starknetKeccak()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../constants.js` (imported)
- `../../scure-starknet/index.js` (imported)
- `../types/index.js` (imported)
- `./encode.js` (imported)
- `./num.js` (imported)
- `../constants.js` (referenced)
- `../../scure-starknet/index.js` (referenced)
- `../types/index.js` (referenced)
- `./encode.js` (referenced)
- `./num.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/utils/selector.ts
```

