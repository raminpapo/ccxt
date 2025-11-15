# Documentation: ts/src/static_dependencies/starknet/types/cairoEnum.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/types/cairoEnum.ts`
- **Size**: 178 bytes
- **Lines**: 4
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { CairoCustomEnum, CairoOption, CairoResult } from '../utils/calldata/enum/index.js';

export type CairoEnum = CairoCustomEnum | CairoOption<any> | CairoResult<any, any>;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/types/cairoEnum.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 4
- Code lines: 2
- Comment lines: 0
- Blank lines: 2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../utils/calldata/enum/index.js` (imported)
- `../utils/calldata/enum/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/starknet/types/cairoEnum.ts
```

