# Documentation: ts/src/static_dependencies/starknet/utils/hash/index.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/hash/index.ts`
- **Size**: 246 bytes
- **Lines**: 9
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * Hashes Exports
 */
export * as poseidon from '../../../noble-curves/abstract/poseidon.js';
export * from '../selector.js'; // Preserve legacy export structure

// export * from './transactionHash/index.js';
export * from './classHash.js';

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/hash/index.ts`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 9
- Code lines: 6
- Comment lines: 4
- Blank lines: -1

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

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/utils/hash/index.ts
```

