# Documentation: ts/src/static_dependencies/starknet/utils/uint256.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/uint256.ts`
- **Size**: 808 bytes
- **Lines**: 33
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/* eslint-disable no-bitwise */
import { BigNumberish, Uint256 } from '../types/index.js';
import { CairoUint256, UINT_128_MAX, UINT_256_MAX } from './cairoDataTypes/uint256.js';

/**
 * @deprecated Legacy support Export
 */
export { UINT_128_MAX, UINT_256_MAX };

/**
 * Convert Uint256 to bigint
 * Legacy support Export
 */
export function uint256ToBN(uint256: Uint256) {
  return new CairoUint256(uint256).toBigInt();
}

/**
 * Test BigNumberish is smaller or equal 2**256-1
 * Legacy support Export
 */
export function isUint256(bn: BigNumberish): boolean {
  return CairoUint256.is(bn);
}

/**
 * Convert BigNumberish (string | number | bigint) to Uint256 (hex)
 * Legacy support Export
 */
export function bnToUint256(bn: BigNumberish): Uint256 {
  return new CairoUint256(bn).toUint256HexString();
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/uint256.ts`.

**Functions defined**: isUint256, bnToUint256, uint256ToBN

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 28
- Comment lines: 16
- Blank lines: -11

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
ts-node ts/src/static_dependencies/starknet/utils/uint256.ts
```

