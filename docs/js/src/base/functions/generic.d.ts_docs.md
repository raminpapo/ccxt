# Documentation: js/src/base/functions/generic.d.ts

## File Metadata

- **Path**: `js/src/base/functions/generic.d.ts`
- **Size**: 1,966 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Dictionary, IndexType } from '../types.js';
declare const keys: {
    (o: object): string[];
    (o: {}): string[];
};
declare const values: (x: any[] | Dictionary<any>) => any[];
declare const index: (x: any[]) => Set<any>;
declare const extend: (...args: any[]) => any;
declare const clone: (x: any) => any;
declare const ordered: (x: any[] | Dictionary<any>) => any[] | Dictionary<any>;
declare const unique: (x: any[]) => any[];
declare const arrayConcat: (a: any[], b: any[]) => any[];
declare const inArray: (needle: any, haystack: any[]) => boolean;
declare const toArray: (object: Dictionary<any> | any[]) => any[];
declare const isEmpty: (object: any[] | Dictionary<any>) => boolean;
declare const keysort: (x: Dictionary<any>, out?: Dictionary<any>) => Dictionary<any>;
declare const sort: (array: string[] | any) => any;
declare const groupBy: (x: Dictionary<any>, k: string, out?: Dictionary<any>) => Dictionary<any>;
declare const indexBy: (x: Dictionary<any>, k: IndexType, out?: Dictionary<any>) => Dictionary<any>;
declare const filterBy: (x: Dictionary<any>, k: string, value?: any, out?: Dictionary<any>[]) => Dictionary<any>[];
declare const sortBy: (array: any[], key: IndexType, descending?: boolean, defaultValue?: any, direction?: number) => any[];
declare const sortBy2: (array: any[], key1: IndexType, key2: IndexType, descending?: boolean, direction?: number) => any[];
declare const flatten: (x: any[], out?: any[]) => any[];
declare const pluck: (x: Dictionary<any>, k: any) => any[];
declare const omit: (x: Dictionary<any>, ...args: any) => any;
declare const sum: (...xs: any[]) => any;
declare const deepExtend: (...xs: any) => any;
declare const merge: (target: Dictionary<any>, ...args: any) => Dictionary<any>;
export { keys, values, extend, clone, index, ordered, unique, arrayConcat, inArray, toArray, isEmpty, sort, keysort, indexBy, groupBy, filterBy, sortBy, sortBy2, flatten, pluck, omit, sum, deepExtend, merge, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/generic.d.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 29
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../types.js` (imported)
- `../types.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/functions/generic.d.ts
```

