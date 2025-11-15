# Documentation: js/src/static_dependencies/node-fetch/errors/fetch-error.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/errors/fetch-error.d.ts`
- **Size**: 887 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * @typedef {{ address?: string, code: string, dest?: string, errno: number, info?: object, message: string, path?: string, port?: number, syscall: string}} SystemError
*/
/**
 * FetchError interface for operational errors
 */
export class FetchError extends FetchBaseError {
    /**
     * @param  {string} message -      Error message for human
     * @param  {string} [type] -        Error type for machine
     * @param  {SystemError} [systemError] - For Node.js system error
     */
    constructor(message: string, type?: string, systemError?: SystemError);
    code: string;
    errno: string;
    erroredSysCall: string;
}
export type SystemError = {
    address?: string;
    code: string;
    dest?: string;
    errno: number;
    info?: object;
    message: string;
    path?: string;
    port?: number;
    syscall: string;
};
import { FetchBaseError } from "./base.js";

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/node-fetch/errors/fetch-error.d.ts`.

**Classes defined**: FetchError

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 29
- Comment lines: 11
- Blank lines: -10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./base.js` (imported)
- `./base.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/node-fetch/errors/fetch-error.d.ts
```

