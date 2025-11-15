# Documentation: js/src/base/functions/type.d.ts

## File Metadata

- **Path**: `js/src/base/functions/type.d.ts`
- **Size**: 3,589 bytes
- **Lines**: 38
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType, Int, Str, IndexType, Num } from '../types.js';
declare const isNumber: (number: unknown) => boolean;
declare const isInteger: (number: unknown) => boolean;
declare const isArray: (arg: any) => arg is any[];
declare const hasProps: (o: any) => boolean;
declare const isString: (s: any) => boolean;
declare const isObject: (o: any) => boolean;
declare const isDictionary: (o: any) => boolean;
declare const isStringCoercible: (x: any) => any;
declare const prop: (o: any, k: IndexType) => any;
declare const asFloat: (x: any) => number | typeof NaN;
declare const asInteger: (x: any) => number | typeof NaN;
declare const safeFloat: (o: implicitReturnType, k: IndexType, $default?: number) => Num;
declare const safeInteger: (o: implicitReturnType, k: IndexType, $default?: number) => Int;
declare const safeIntegerProduct: (o: implicitReturnType, k: IndexType, $factor: number, $default?: number) => Int;
declare const safeTimestamp: (o: implicitReturnType, k: IndexType, $default?: number) => Int;
declare const safeValue: (o: implicitReturnType, k: IndexType, $default?: any) => any;
declare const safeString: (o: implicitReturnType, k: IndexType, $default?: string) => Str;
declare const safeStringLower: (o: implicitReturnType, k: IndexType, $default?: string) => Str;
declare const safeStringUpper: (o: implicitReturnType, k: IndexType, $default?: string) => Str;
declare const safeFloat2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $default?: number) => Num;
declare const safeInteger2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $default?: number) => Int;
declare const safeIntegerProduct2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $factor: number, $default?: number) => Int;
declare const safeTimestamp2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $default?: Int) => Int;
declare const safeValue2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $default?: any) => any;
declare const safeString2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $default?: string) => Str;
declare const safeStringLower2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $default?: string) => Str;
declare const safeStringUpper2: (o: implicitReturnType, k1: IndexType, k2: IndexType, $default?: string) => Str;
declare const safeFloatN: (o: implicitReturnType, k: (IndexType)[], $default?: number) => Num;
declare const safeIntegerN: (o: implicitReturnType, k: (IndexType)[], $default?: number) => Int;
declare const safeIntegerProductN: (o: implicitReturnType, k: (IndexType)[], $factor: number, $default?: number) => Int;
declare const safeTimestampN: (o: implicitReturnType, k: (IndexType)[], $default?: number) => Int;
declare const safeValueN: (o: implicitReturnType, k: (IndexType)[], $default?: any) => any;
declare const safeStringN: (o: implicitReturnType, k: (IndexType)[], $default?: string) => Str;
declare const safeStringLowerN: (o: implicitReturnType, k: (IndexType)[], $default?: string) => Str;
declare const safeStringUpperN: (o: implicitReturnType, k: (IndexType)[], $default?: string) => Str;
export { isNumber, isInteger, isArray, isObject, isString, isStringCoercible, isDictionary, hasProps, prop, asFloat, asInteger, safeFloat, safeInteger, safeIntegerProduct, safeTimestamp, safeValue, safeString, safeStringLower, safeStringUpper, safeFloat2, safeInteger2, safeIntegerProduct2, safeTimestamp2, safeValue2, safeString2, safeStringLower2, safeStringUpper2, safeFloatN, safeIntegerN, safeIntegerProductN, safeTimestampN, safeValueN, safeStringN, safeStringLowerN, safeStringUpperN, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/type.d.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 37
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
ts-node js/src/base/functions/type.d.ts
```

