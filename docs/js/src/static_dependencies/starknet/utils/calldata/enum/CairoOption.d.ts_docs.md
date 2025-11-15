# Documentation: js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.d.ts`
- **Size**: 915 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare enum CairoOptionVariant {
    Some = 0,
    None = 1
}
/**
 * Class to handle Cairo Option
 * @param variant CairoOptionVariant.Some or CairoOptionVariant.None
 * @param someContent value of type T.
 * @returns an instance representing a Cairo Option.
 * @example
 * ```typescript
 * const myOption = new CairoOption<BigNumberish>(CairoOptionVariant.Some, "0x54dda8");
 * ```
 */
export declare class CairoOption<T> {
    readonly Some?: T;
    readonly None?: boolean;
    constructor(variant: CairoOptionVariant, someContent?: T);
    /**
     *
     * @returns the content of the valid variant of a Cairo custom Enum.
     *  If None, returns 'undefined'.
     */
    unwrap(): T | undefined;
    /**
     *
     * @returns true if the valid variant is 'isSome'.
     */
    isSome(): boolean;
    /**
     *
     * @returns true if the valid variant is 'isNone'.
     */
    isNone(): boolean;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.d.ts`.

**Classes defined**: CairoOption

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 35
- Comment lines: 23
- Blank lines: -22

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
ts-node js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.d.ts
```

