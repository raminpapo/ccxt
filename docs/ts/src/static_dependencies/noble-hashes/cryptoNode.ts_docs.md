# Documentation: ts/src/static_dependencies/noble-hashes/cryptoNode.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/noble-hashes/cryptoNode.ts`
- **Size**: 146 bytes
- **Lines**: 4
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import * as nc from 'node:crypto';
export const crypto =
  nc && typeof nc === 'object' && 'webcrypto' in nc ? (nc.webcrypto as any) : undefined;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/noble-hashes/cryptoNode.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 4
- Code lines: 3
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `node:crypto` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/noble-hashes/cryptoNode.ts
```

