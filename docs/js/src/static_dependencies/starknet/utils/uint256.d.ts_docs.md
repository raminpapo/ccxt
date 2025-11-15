# Documentation: js/src/static_dependencies/starknet/utils/uint256.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/uint256.d.ts`
- **Size**: 652 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BigNumberish, Uint256 } from '../types/index.js';
import { UINT_128_MAX, UINT_256_MAX } from './cairoDataTypes/uint256.js';
/**
 * @deprecated Legacy support Export
 */
export { UINT_128_MAX, UINT_256_MAX };
/**
 * Convert Uint256 to bigint
 * Legacy support Export
 */
export declare function uint256ToBN(uint256: Uint256): bigint;
/**
 * Test BigNumberish is smaller or equal 2**256-1
 * Legacy support Export
 */
export declare function isUint256(bn: BigNumberish): boolean;
/**
 * Convert BigNumberish (string | number | bigint) to Uint256 (hex)
 * Legacy support Export
 */
export declare function bnToUint256(bn: BigNumberish): Uint256;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/uint256.d.ts`.

**Functions defined**: isUint256, bnToUint256, uint256ToBN

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 21
- Comment lines: 15
- Blank lines: -14

### Main Components

**Functions** (3):
- `bnToUint256()`
- `isUint256()`
- `uint256ToBN()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./cairoDataTypes/uint256.js` (imported)
- `../types/index.js` (imported)
- `./cairoDataTypes/uint256.js` (referenced)
- `../types/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/uint256.d.ts
```

