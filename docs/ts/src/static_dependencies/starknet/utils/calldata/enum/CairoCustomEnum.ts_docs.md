# Documentation: ts/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.ts`
- **Size**: 2,073 bytes
- **Lines**: 69
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export type CairoEnumRaw = {
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
export class CairoCustomEnum {
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
  constructor(enumContent: CairoEnumRaw) {
    const variantsList = Object.values(enumContent);
    if (variantsList.length === 0) {
      throw new Error('This Enum must have at least 1 variant');
    }
    const nbActiveVariants = variantsList.filter(
      (content) => typeof content !== 'undefined'
    ).length;
    if (nbActiveVariants !== 1) {
      throw new Error('This Enum must have exactly one active variant');
    }
    this.variant = enumContent;
  }

  /**
   *
   * @returns the content of the valid variant of a Cairo custom Enum.
   */
  public unwrap(): any {
    const variants = Object.entries(this.variant);
    const activeVariant = variants.find((item) => typeof item[1] !== 'undefined');
    if (typeof activeVariant === 'undefined') {
      return undefined;
    }
    return activeVariant[1];
  }

  /**
   *
   * @returns the name of the valid variant of a Cairo custom Enum.
   */
  public activeVariant(): string {
    const variants = Object.entries(this.variant);
    const activeVariant = variants.find((item) => typeof item[1] !== 'undefined');
    if (typeof activeVariant === 'undefined') {
      return '';
    }
    return activeVariant[0];
  }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.ts`.

**Classes defined**: CairoCustomEnum

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 69
- Code lines: 64
- Comment lines: 29
- Blank lines: -24

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
ts-node ts/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.ts
```

