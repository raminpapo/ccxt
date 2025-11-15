# Documentation: js/src/static_dependencies/starknet/utils/merkle.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/merkle.d.ts`
- **Size**: 1,296 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BigNumberish } from '../types/index.js';
export declare class MerkleTree {
    leaves: string[];
    branches: string[][];
    root: string;
    hashMethod: (a: BigNumberish, b: BigNumberish) => string;
    constructor(leafHashes: string[], hashMethod?: (a: BigNumberish, b: BigNumberish) => string);
    /**
     * Create Merkle tree
     * @param leaves hex-string array
     * @returns format: hex-string; Merkle tree root
     */
    private build;
    /**
     * Create hash from ordered a and b, Pedersen hash default
     * @returns format: hex-string
     */
    static hash(a: BigNumberish, b: BigNumberish, hashMethod?: (a: BigNumberish, b: BigNumberish) => string): string;
    /**
     * Return path to leaf
     * @param leaf hex-string
     * @param branch hex-string array
     * @param hashPath hex-string array
     * @returns format: hex-string array
     */
    getProof(leaf: string, branch?: string[], hashPath?: string[]): string[];
}
/**
 * Test Merkle tree path
 * @param root hex-string
 * @param leaf hex-string
 * @param path hex-string array
 * @param hashMethod hash method override, Pedersen default
 */
export declare function proofMerklePath(root: string, leaf: string, path: string[], hashMethod?: (a: BigNumberish, b: BigNumberish) => string): boolean;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/merkle.d.ts`.

**Classes defined**: MerkleTree

**Functions defined**: proofMerklePath

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 35
- Comment lines: 23
- Blank lines: -22

### Main Components

**Classes** (1):
- `MerkleTree`

**Functions** (1):
- `proofMerklePath()`



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
ts-node js/src/static_dependencies/starknet/utils/merkle.d.ts
```

