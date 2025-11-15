# Documentation: js/src/static_dependencies/starknet/utils/typedData.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/typedData.d.ts`
- **Size**: 2,571 bytes
- **Lines**: 55
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { BigNumberish, TypedDataRevision as Revision, StarknetMerkleType, StarknetType, TypedData } from '../types/index.js';
/** @deprecated prefer importing from 'types' over 'typedData' */
interface Context {
    parent?: string;
    key?: string;
}
/**
 * Prepares the selector for use.
 *
 * @param {string} selector - The selector to be prepared.
 * @returns {string} The prepared selector.
 */
export declare function prepareSelector(selector: string): string;
/**
 * Checks if the given Starknet type is a Merkle tree type.
 *
 * @param {StarknetType} type - The StarkNet type to check.
 *
 * @returns {boolean} - True if the type is a Merkle tree type, false otherwise.
 */
export declare function isMerkleTreeType(type: StarknetType): type is StarknetMerkleType;
/**
 * Get the dependencies of a struct type. If a struct has the same dependency multiple times, it's only included once
 * in the resulting array.
 */
export declare function getDependencies(types: TypedData['types'], type: string, dependencies?: string[], contains?: string, revision?: Revision): string[];
/**
 * Encode a type to a string. All dependent types are alphabetically sorted.
 */
export declare function encodeType(types: TypedData['types'], type: string, revision?: Revision): string;
/**
 * Get a type string as hash.
 */
export declare function getTypeHash(types: TypedData['types'], type: string, revision?: Revision): string;
/**
 * Encodes a single value to an ABI serialisable string, number or Buffer. Returns the data as tuple, which consists of
 * an array of ABI compatible types, and an array of corresponding values.
 */
export declare function encodeValue(types: TypedData['types'], type: string, data: unknown, ctx?: Context, revision?: Revision): [string, string];
/**
 * Encode the data to an ABI encoded Buffer. The data should be a key -> value object with all the required values.
 * All dependent types are automatically encoded.
 */
export declare function encodeData<T extends TypedData>(types: T['types'], type: string, data: T['message'], revision?: Revision): string[][];
/**
 * Get encoded data as a hash. The data should be a key -> value object with all the required values.
 * All dependent types are automatically encoded.
 */
export declare function getStructHash<T extends TypedData>(types: T['types'], type: string, data: T['message'], revision?: Revision): string;
/**
 * Get the SNIP-12 encoded message to sign, from the typedData object.
 */
export declare function getMessageHash(typedData: TypedData, account: BigNumberish): string;
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/typedData.d.ts`.

**Functions defined**: getStructHash, encodeType, getDependencies, isMerkleTreeType, getMessageHash, prepareSelector, getTypeHash, encodeValue, encodeData

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 54
- Comment lines: 39
- Blank lines: -38

### Main Components

**Functions** (9):
- `encodeData()`
- `encodeType()`
- `encodeValue()`
- `getDependencies()`
- `getMessageHash()`
- `getStructHash()`
- `getTypeHash()`
- `isMerkleTreeType()`
- `prepareSelector()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `types` (imported)
- `../types/index.js` (imported)
- `../types/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/typedData.d.ts
```

