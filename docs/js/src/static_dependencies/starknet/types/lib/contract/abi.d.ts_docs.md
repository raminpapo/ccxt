# Documentation: js/src/static_dependencies/starknet/types/lib/contract/abi.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/lib/contract/abi.d.ts`
- **Size**: 1,623 bytes
- **Lines**: 72
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/** ABI */
export declare type Abi = ReadonlyArray<FunctionAbi | EventAbi | StructAbi | InterfaceAbi | any>;
export declare type AbiEntry = {
    name: string;
    type: 'felt' | 'felt*' | string;
};
export declare type EventEntry = {
    name: string;
    type: 'felt' | 'felt*' | string;
    kind: 'key' | 'data';
};
declare enum FunctionAbiType {
    'function' = 0,
    'l1_handler' = 1,
    'constructor' = 2
}
export declare type FunctionAbi = {
    inputs: AbiEntry[];
    name: string;
    outputs: AbiEntry[];
    stateMutability?: 'view';
    state_mutability?: string;
    type: FunctionAbiType;
};
export declare type AbiStructs = {
    [name: string]: StructAbi;
};
export declare type StructAbi = {
    members: (AbiEntry & {
        offset: number;
    })[];
    name: string;
    size: number;
    type: 'struct';
};
export declare type AbiInterfaces = {
    [name: string]: InterfaceAbi;
};
export declare type InterfaceAbi = {
    items: FunctionAbi[];
    name: string;
    type: 'interface';
};
export declare type AbiEnums = {
    [name: string]: EnumAbi;
};
export declare type EnumAbi = {
    variants: (AbiEntry & {
        offset: number;
    })[];
    name: string;
    size: number;
    type: 'enum/index.js';
};
export declare type AbiEvents = {
    [hash: string]: EventAbi;
};
export declare type EventAbi = Cairo1Event | LegacyEvent;
export declare type Cairo1Event = {
    name: string;
    members: EventEntry[];
    kind: 'struct';
    type: 'event';
};
export declare type LegacyEvent = {
    name: string;
    type: 'event';
    data: EventEntry[];
    keys: EventEntry[];
};
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/lib/contract/abi.d.ts`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 71
- Comment lines: 1
- Blank lines: 0

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
ts-node js/src/static_dependencies/starknet/types/lib/contract/abi.d.ts
```

