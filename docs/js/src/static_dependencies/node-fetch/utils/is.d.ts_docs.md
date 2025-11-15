# Documentation: js/src/static_dependencies/node-fetch/utils/is.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/utils/is.d.ts`
- **Size**: 349 bytes
- **Lines**: 6
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export function isURLSearchParameters(object: any): boolean;
export function isBlob(object: any): boolean;
export function isAbortSignal(object: any): boolean;
export function isDomainOrSubdomain(destination: string | URL, original: string | URL): boolean;
export function isSameProtocol(destination: string | URL, original: string | URL): boolean;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/node-fetch/utils/is.d.ts`.

**Functions defined**: isAbortSignal, isSameProtocol, isURLSearchParameters, isBlob, isDomainOrSubdomain



## Detailed Walkthrough

### Code Structure

- Total lines: 6
- Code lines: 5
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (5):
- `isAbortSignal()`
- `isBlob()`
- `isDomainOrSubdomain()`
- `isSameProtocol()`
- `isURLSearchParameters()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/node-fetch/utils/is.d.ts
```

