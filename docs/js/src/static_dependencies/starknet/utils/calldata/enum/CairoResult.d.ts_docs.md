# Documentation: js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.d.ts`
- **Size**: 867 bytes
- **Lines**: 35
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare enum CairoResultVariant {
    Ok = 0,
    Err = 1
}
/**
 * Class to handle Cairo Result
 * @param variant CairoResultVariant.Ok or CairoResultVariant.Err
 * @param resultContent value of type T or U.
 * @returns an instance representing a Cairo Result.
 * @example
 * ```typescript
 * const myOption = new CairoResult<BigNumberish, CustomError>(CairoResultVariant.Ok, "0x54dda8");
 * ```
 */
export declare class CairoResult<T, U> {
    readonly Ok?: T;
    readonly Err?: U;
    constructor(variant: CairoResultVariant, resultContent: T | U);
    /**
     *
     * @returns the content of the valid variant of a Cairo Result.
     */
    unwrap(): T | U;
    /**
     *
     * @returns true if the valid variant is 'Ok'.
     */
    isOk(): boolean;
    /**
     *
     * @returns true if the valid variant is 'isErr'.
     */
    isErr(): boolean;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.d.ts`.

**Classes defined**: CairoResult

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 34
- Comment lines: 22
- Blank lines: -21

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.d.ts
```

