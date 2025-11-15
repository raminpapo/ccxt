# Documentation: js/src/base/ws/Cache.d.ts

## File Metadata

- **Path**: `js/src/base/ws/Cache.d.ts`
- **Size**: 846 bytes
- **Lines**: 28
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
interface CustomArray extends Array<any> {
    hashmap: object;
}
declare class BaseCache extends Array {
    constructor(maxSize?: any);
    clear(): void;
}
declare class ArrayCache extends BaseCache implements CustomArray {
    hashmap: object;
    constructor(maxSize?: any);
    getLimit(symbol: any, limit: any): any;
    append(item: any): void;
}
declare class ArrayCacheByTimestamp extends BaseCache {
    constructor(maxSize?: any);
    getLimit(symbol: any, limit: any): any;
    append(item: any): void;
}
declare class ArrayCacheBySymbolById extends ArrayCache {
    constructor(maxSize?: any);
    append(item: any): void;
}
declare class ArrayCacheBySymbolBySide extends ArrayCache {
    constructor();
    append(item: any): void;
}
export { ArrayCache, ArrayCacheByTimestamp, ArrayCacheBySymbolById, ArrayCacheBySymbolBySide, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/ws/Cache.d.ts`.

**Classes defined**: ArrayCacheBySymbolBySide, ArrayCacheBySymbolById, ArrayCache, ArrayCacheByTimestamp, BaseCache



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 27
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/ws/Cache.d.ts
```

