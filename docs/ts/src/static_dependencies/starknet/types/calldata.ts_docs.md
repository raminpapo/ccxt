# Documentation: ts/src/static_dependencies/starknet/types/calldata.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/types/calldata.ts`
- **Size**: 585 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export enum ValidateType {
  DEPLOY = 'DEPLOY',
  CALL = 'CALL',
  INVOKE = 'INVOKE',
}

export enum Uint {
  u8 = 'core::integer::u8',
  u16 = 'core::integer::u16',
  u32 = 'core::integer::u32',
  u64 = 'core::integer::u64',
  u128 = 'core::integer::u128',
  u256 = 'core::integer::u256', // This one is struct
  u512 = 'core::integer::u512', // This one is struct
}

export enum Literal {
  ClassHash = 'core::starknet::class_hash::ClassHash',
  ContractAddress = 'core::starknet::contract_address::ContractAddress',
  Secp256k1Point = 'core::starknet::secp256k1::Secp256k1Point',
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/types/calldata.ts`.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 19
- Comment lines: 0
- Blank lines: 3

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
ts-node ts/src/static_dependencies/starknet/types/calldata.ts
```

