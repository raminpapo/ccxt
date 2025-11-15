# Documentation: js/src/static_dependencies/starknet/utils/uint256.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/uint256.js`
- **Size**: 664 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { CairoUint256, UINT_128_MAX, UINT_256_MAX } from './cairoDataTypes/uint256.js';
/**
 * @deprecated Legacy support Export
 */
export { UINT_128_MAX, UINT_256_MAX };
/**
 * Convert Uint256 to bigint
 * Legacy support Export
 */
export function uint256ToBN(uint256) {
    return new CairoUint256(uint256).toBigInt();
}
/**
 * Test BigNumberish is smaller or equal 2**256-1
 * Legacy support Export
 */
export function isUint256(bn) {
    return CairoUint256.is(bn);
}
/**
 * Convert BigNumberish (string | number | bigint) to Uint256 (hex)
 * Legacy support Export
 */
export function bnToUint256(bn) {
    return new CairoUint256(bn).toUint256HexString();
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/uint256.js`.

**Functions defined**: isUint256, bnToUint256, uint256ToBN

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 26
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
- `./cairoDataTypes/uint256.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/uint256.js
```

