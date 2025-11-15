# Documentation: js/src/static_dependencies/starknet/types/typedData.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/typedData.d.ts`
- **Size**: 1,360 bytes
- **Lines**: 45
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare const TypedDataRevision: {
    readonly Active: "1";
    readonly Legacy: "0";
};
export declare type TypedDataRevision = (typeof TypedDataRevision)[keyof typeof TypedDataRevision];
export declare type StarknetEnumType = {
    name: string;
    type: 'enum';
    contains: string;
};
export declare type StarknetMerkleType = {
    name: string;
    type: 'merkletree';
    contains: string;
};
/**
 * SPEC: STARKNET_TYPE
 * A single type, as part of a struct. The `type` field can be any of the EIP-712 supported types.
 * Note that the `uint` and `int` aliases like in Solidity, and fixed point numbers are not supported by the EIP-712
 * standard.
 */
export declare type StarknetType = {
    name: string;
    type: string;
} | StarknetEnumType | StarknetMerkleType;
/**
 * The EIP712 domain struct. Any of these fields are optional, but it must contain at least one field.
 */
export interface StarknetDomain extends Record<string, unknown> {
    name?: string;
    version?: string;
    chainId?: string | number;
    revision?: string | number;
}
/**
 * SPEC: TYPED_DATA
 * The complete typed data, with all the structs, domain data, primary type of the message, and the message itself.
 */
export interface TypedData {
    types: Record<string, StarknetType[]>;
    primaryType: string;
    domain: StarknetDomain;
    message: object;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/typedData.d.ts`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 44
- Comment lines: 13
- Blank lines: -12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/types/typedData.d.ts
```

