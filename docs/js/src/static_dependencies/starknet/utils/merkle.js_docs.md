# Documentation: js/src/static_dependencies/starknet/utils/merkle.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/merkle.js`
- **Size**: 2,850 bytes
- **Lines**: 79
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import { computePedersenHash } from './hash/index.js';
export class MerkleTree {
    constructor(leafHashes, hashMethod = computePedersenHash) {
        this.branches = [];
        this.hashMethod = hashMethod;
        this.leaves = leafHashes;
        this.root = this.build(leafHashes);
    }
    /**
     * Create Merkle tree
     * @param leaves hex-string array
     * @returns format: hex-string; Merkle tree root
     */
    build(leaves) {
        if (leaves.length === 1) {
            return leaves[0];
        }
        if (leaves.length !== this.leaves.length) {
            this.branches.push(leaves);
        }
        const newLeaves = [];
        for (let i = 0; i < leaves.length; i += 2) {
            if (i + 1 === leaves.length) {
                newLeaves.push(MerkleTree.hash(leaves[i], '0x0', this.hashMethod));
            }
            else {
                newLeaves.push(MerkleTree.hash(leaves[i], leaves[i + 1], this.hashMethod));
            }
        }
        return this.build(newLeaves);
    }
    /**
     * Create hash from ordered a and b, Pedersen hash default
     * @returns format: hex-string
     */
    static hash(a, b, hashMethod = computePedersenHash) {
        const [aSorted, bSorted] = [BigInt(a), BigInt(b)].sort((x, y) => (x >= y ? 1 : -1));
        return hashMethod(aSorted, bSorted);
    }
    /**
     * Return path to leaf
     * @param leaf hex-string
     * @param branch hex-string array
     * @param hashPath hex-string array
     * @returns format: hex-string array
     */
    getProof(leaf, branch = this.leaves, hashPath = []) {
        const index = branch.indexOf(leaf);
        if (index === -1) {
            throw new Error('leaf not found');
        }
        if (branch.length === 1) {
            return hashPath;
        }
        const isLeft = index % 2 === 0;
        const neededBranch = (isLeft ? branch[index + 1] : branch[index - 1]) ?? '0x0';
        const newHashPath = [...hashPath, neededBranch];
        const currentBranchLevelIndex = this.leaves.length === branch.length
            ? -1
            : this.branches.findIndex((b) => b.length === branch.length);
        const nextBranch = this.branches[currentBranchLevelIndex + 1] ?? [this.root];
        return this.getProof(MerkleTree.hash(isLeft ? leaf : neededBranch, isLeft ? neededBranch : leaf, this.hashMethod), nextBranch, newHashPath);
    }
}
/**
 * Test Merkle tree path
 * @param root hex-string
 * @param leaf hex-string
 * @param path hex-string array
 * @param hashMethod hash method override, Pedersen default
 */
export function proofMerklePath(root, leaf, path, hashMethod = computePedersenHash) {
    if (path.length === 0) {
        return root === leaf;
    }
    const [next, ...rest] = path;
    return proofMerklePath(root, MerkleTree.hash(leaf, next, hashMethod), rest, hashMethod);
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/merkle.js`.

**Classes defined**: MerkleTree

**Functions defined**: proofMerklePath

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 79
- Code lines: 78
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

- `./hash/index.js` (imported)
- `./hash/index.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/merkle.js
```

