# Documentation: js/src/static_dependencies/starknet/utils/calldata/propertyOrder.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/propertyOrder.d.ts`
- **Size**: 230 bytes
- **Lines**: 3
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { AbiEntry, AbiEnums, AbiStructs, RawArgsObject } from '../../types/index.js';
export default function orderPropsByAbi(unorderedObject: RawArgsObject, abiOfObject: AbiEntry[], structs: AbiStructs, enums: AbiEnums): object;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/propertyOrder.d.ts`.

**Functions defined**: orderPropsByAbi

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 3
- Code lines: 2
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (1):
- `orderPropsByAbi()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../types/index.js` (imported)
- `../../types/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/calldata/propertyOrder.d.ts
```

