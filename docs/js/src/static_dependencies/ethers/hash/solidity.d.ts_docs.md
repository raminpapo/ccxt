# Documentation: js/src/static_dependencies/ethers/hash/solidity.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/hash/solidity.d.ts`
- **Size**: 1,178 bytes
- **Lines**: 31
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 *   Computes the [[link-solc-packed]] representation of %%values%%
 *   respectively to their %%types%%.
 *
 *   @example:
 *       addr = "0x8ba1f109551bd432803012645ac136ddd64dba72"
 *       solidityPacked([ "address", "uint" ], [ addr, 45 ]);
 *       //_result:
 */
export declare function solidityPacked(types: ReadonlyArray<string>, values: ReadonlyArray<any>): string;
/**
 *   Computes the [[link-solc-packed]] [[keccak256]] hash of %%values%%
 *   respectively to their %%types%%.
 *
 *   @example:
 *       addr = "0x8ba1f109551bd432803012645ac136ddd64dba72"
 *       solidityPackedKeccak256([ "address", "uint" ], [ addr, 45 ]);
 *       //_result:
 */
export declare function solidityPackedKeccak256(types: ReadonlyArray<string>, values: ReadonlyArray<any>): string;
/**
 *   Computes the [[link-solc-packed]] [[sha256]] hash of %%values%%
 *   respectively to their %%types%%.
 *
 *   @example:
 *       addr = "0x8ba1f109551bd432803012645ac136ddd64dba72"
 *       solidityPackedSha256([ "address", "uint" ], [ addr, 45 ]);
 *       //_result:
 */
export declare function solidityPackedSha256(types: ReadonlyArray<string>, values: ReadonlyArray<any>): string;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/hash/solidity.d.ts`.

**Functions defined**: solidityPackedSha256, solidityPackedKeccak256, solidityPacked

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 30
- Comment lines: 27
- Blank lines: -26

### Main Components

**Functions** (3):
- `solidityPacked()`
- `solidityPackedKeccak256()`
- `solidityPackedSha256()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/hash/solidity.d.ts
```

