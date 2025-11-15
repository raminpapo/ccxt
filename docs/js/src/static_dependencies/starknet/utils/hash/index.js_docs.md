# Documentation: js/src/static_dependencies/starknet/utils/hash/index.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/hash/index.js`
- **Size**: 245 bytes
- **Lines**: 8
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
/**
 * Hashes Exports
 */
export * as poseidon from '../../../noble-curves/abstract/poseidon.js';
export * from '../selector.js'; // Preserve legacy export structure
// export * from './transactionHash/index.js';
export * from './classHash.js';

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/hash/index.js`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 8
- Code lines: 6
- Comment lines: 4
- Blank lines: -2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../noble-curves/abstract/poseidon.js` (imported)
- `../selector.js` (imported)
- `./classHash.js` (imported)
- `./transactionHash/index.js` (imported)
- `../../../noble-curves/abstract/poseidon.js` (referenced)
- `../selector.js` (referenced)
- `./classHash.js` (referenced)
- `./transactionHash/index.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/hash/index.js
```

