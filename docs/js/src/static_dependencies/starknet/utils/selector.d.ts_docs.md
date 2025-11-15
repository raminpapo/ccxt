# Documentation: js/src/static_dependencies/starknet/utils/selector.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/selector.d.ts`
- **Size**: 1,680 bytes
- **Lines**: 49
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BigNumberish } from '../types/index.js';
/**
 * Calculate hex-string keccak hash for a given BigNumberish
 *
 * BigNumberish -> hex-string keccak hash
 * @returns format: hex-string
 */
export declare function keccakBn(value: BigNumberish): string;
/**
 * Calculate bigint keccak hash for a given string
 *
 * String -> bigint keccak hash
 *
 * [Reference](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/public/abi.py#L17-L22)
 * @param str the value you want to get the keccak hash from
 * @returns starknet keccak hash as BigInt
 */
export declare function starknetKeccak(str: string): bigint;
/**
 * Calculate hex-string selector for a given abi-function-name
 *
 * Abi-function-name -> hex-string selector
 *
 * [Reference](https://github.com/starkware-libs/cairo-lang/blob/master/src/starkware/starknet/public/abi.py#L25-L26)
 * @param funcName ascii-string of 'abi function name'
 * @returns format: hex-string; selector for 'abi function name'
 */
export declare function getSelectorFromName(funcName: string): string;
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
export declare function getSelector(value: string): string;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/selector.d.ts`.

**Functions defined**: getSelector, keccakBn, getSelectorFromName, starknetKeccak, name

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 48
- Comment lines: 43
- Blank lines: -42

### Main Components

**Functions** (5):
- `getSelector()`
- `getSelectorFromName()`
- `keccakBn()`
- `name()`
- `starknetKeccak()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../types/index.js` (imported)
- `../types/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/selector.d.ts
```

