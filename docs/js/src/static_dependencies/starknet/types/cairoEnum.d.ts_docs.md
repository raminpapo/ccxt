# Documentation: js/src/static_dependencies/starknet/types/cairoEnum.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/cairoEnum.d.ts`
- **Size**: 185 bytes
- **Lines**: 3
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { CairoCustomEnum, CairoOption, CairoResult } from '../utils/calldata/enum/index.js';
export declare type CairoEnum = CairoCustomEnum | CairoOption<any> | CairoResult<any, any>;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/types/cairoEnum.d.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 3
- Code lines: 2
- Comment lines: 0
- Blank lines: 1

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
ts-node js/src/static_dependencies/starknet/types/cairoEnum.d.ts
```

