# Documentation: ts/src/static_dependencies/starknet/types/lib/contract/abi.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/types/lib/contract/abi.ts`
- **Size**: 1,418 bytes
- **Lines**: 66
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/** ABI */
export type Abi = ReadonlyArray<FunctionAbi | EventAbi | StructAbi | InterfaceAbi | any>;

// Basic elements
export type AbiEntry = { name: string; type: 'felt' | 'felt*' | string };

export type EventEntry = { name: string; type: 'felt' | 'felt*' | string; kind: 'key' | 'data' };

enum FunctionAbiType {
  'function',
  'l1_handler',
  'constructor',
}

// Sub elements
export type FunctionAbi = {
  inputs: AbiEntry[];
  name: string;
  outputs: AbiEntry[];
  stateMutability?: 'view';
  state_mutability?: string; // Cairo 1 Abi
  type: FunctionAbiType;
};

export type AbiStructs = { [name: string]: StructAbi };

export type StructAbi = {
  members: (AbiEntry & { offset: number })[];
  name: string;
  size: number;
  type: 'struct';
};

export type AbiInterfaces = { [name: string]: InterfaceAbi };
export type InterfaceAbi = {
  items: FunctionAbi[];
  name: string;
  type: 'interface';
};

export type AbiEnums = { [name: string]: EnumAbi };
export type EnumAbi = {
  variants: (AbiEntry & { offset: number })[];
  name: string;
  size: number;
  type: 'enum/index.js';
};

export type AbiEvents = { [hash: string]: EventAbi };

export type EventAbi = Cairo1Event | LegacyEvent;

export type Cairo1Event = {
  name: string;
  members: EventEntry[];
  kind: 'struct';
  type: 'event';
};

export type LegacyEvent = {
  name: string;
  type: 'event';
  data: EventEntry[];
  keys: EventEntry[];
};

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/types/lib/contract/abi.ts`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 51
- Comment lines: 3
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `enum/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/types/lib/contract/abi.ts
```

