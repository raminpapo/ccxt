# Documentation: js/src/static_dependencies/starknet/types/calldata.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/calldata.d.ts`
- **Size**: 586 bytes
- **Lines**: 20
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare enum ValidateType {
    DEPLOY = "DEPLOY",
    CALL = "CALL",
    INVOKE = "INVOKE"
}
export declare enum Uint {
    u8 = "core::integer::u8",
    u16 = "core::integer::u16",
    u32 = "core::integer::u32",
    u64 = "core::integer::u64",
    u128 = "core::integer::u128",
    u256 = "core::integer::u256",
    u512 = "core::integer::u512"
}
export declare enum Literal {
    ClassHash = "core::starknet::class_hash::ClassHash",
    ContractAddress = "core::starknet::contract_address::ContractAddress",
    Secp256k1Point = "core::starknet::secp256k1::Secp256k1Point"
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/calldata.d.ts`.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 19
- Comment lines: 0
- Blank lines: 1

### Main Components

**Constants** (3):
- `CALL`
- `DEPLOY`
- `INVOKE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/types/calldata.d.ts
```

