# Documentation: js/src/static_dependencies/ethers/utils/properties.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/properties.d.ts`
- **Size**: 584 bytes
- **Lines**: 23
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 *  Property helper functions.
 *
 *  @_subsection api/utils:Properties  [about-properties]
 */
/**
 *  Resolves to a new object that is a copy of %%value%%, but with all
 *  values resolved.
 */
export declare function resolveProperties<T>(value: {
    [P in keyof T]: T[P] | Promise<T[P]>;
}): Promise<T>;
/**
 *  Assigns the %%values%% to %%target%% as read-only values.
 *
 *  It %%types%% is specified, the values are checked.
 */
export declare function defineProperties<T>(target: T, values: {
    [K in keyof T]?: T[K];
}, types?: {
    [K in keyof T]?: string;
}): void;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/utils/properties.d.ts`.

**Functions defined**: defineProperties, resolveProperties

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 22
- Comment lines: 14
- Blank lines: -13

### Main Components

**Functions** (2):
- `defineProperties()`
- `resolveProperties()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/utils/properties.d.ts
```

