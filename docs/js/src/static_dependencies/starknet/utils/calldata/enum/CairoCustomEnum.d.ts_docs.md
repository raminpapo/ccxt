# Documentation: js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.d.ts`
- **Size**: 1,207 bytes
- **Lines**: 39
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export declare type CairoEnumRaw = {
    [key: string]: any;
};
/**
 * Class to handle Cairo custom Enum
 * @param enumContent object containing the variants and its content. Example :
 *  {Success: 234, Warning: undefined, Error: undefined}.
 *  Only one variant with a value, object, array.
 * @returns an instance representing a Cairo custom Enum.
 * @example
 * ```typescript
 * const myCairoEnum = new CairoCustomEnum( {Success: undefined, Warning: "0x7f32ea", Error: undefined})
 * ```
 */
export declare class CairoCustomEnum {
    /**
     * direct readonly access to variants of the Cairo Custom Enum.
     * @returns a value of type any
     * @example
     * ```typescript
     * const successValue = myCairoEnum.variant.Success;
     */
    readonly variant: CairoEnumRaw;
    /**
     * @param enumContent an object with the variants as keys and the content as value. Only one content shall be defined.
     */
    constructor(enumContent: CairoEnumRaw);
    /**
     *
     * @returns the content of the valid variant of a Cairo custom Enum.
     */
    unwrap(): any;
    /**
     *
     * @returns the name of the valid variant of a Cairo custom Enum.
     */
    activeVariant(): string;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.d.ts`.

**Classes defined**: CairoCustomEnum

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 38
- Comment lines: 29
- Blank lines: -28

### Main Components

**Classes** (1):
- `CairoCustomEnum`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.d.ts
```

