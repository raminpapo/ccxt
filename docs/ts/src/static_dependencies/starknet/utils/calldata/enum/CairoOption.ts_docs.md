# Documentation: ts/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.ts`
- **Size**: 1,553 bytes
- **Lines**: 67
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
export enum CairoOptionVariant {
  Some = 0,
  None = 1,
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
export class CairoOption<T> {
  readonly Some?: T;

  readonly None?: boolean;

  constructor(variant: CairoOptionVariant, someContent?: T) {
    if (!(variant in CairoOptionVariant)) {
      throw new Error('Wrong variant : should be CairoOptionVariant.Some or .None.');
    }
    if (variant === CairoOptionVariant.Some) {
      if (typeof someContent === 'undefined') {
        throw new Error(
          'The creation of a Cairo Option with "Some" variant needs a content as input.'
        );
      }
      this.Some = someContent;
      this.None = undefined;
    } else {
      this.Some = undefined;
      this.None = true;
    }
  }

  /**
   *
   * @returns the content of the valid variant of a Cairo custom Enum.
   *  If None, returns 'undefined'.
   */
  public unwrap(): T | undefined {
    if (this.None) {
      return undefined;
    }
    return this.Some;
  }

  /**
   *
   * @returns true if the valid variant is 'isSome'.
   */
  public isSome(): boolean {
    return !(typeof this.Some === 'undefined');
  }

  /**
   *
   * @returns true if the valid variant is 'isNone'.
   */
  public isNone(): boolean {
    return this.None === true;
  }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.ts`.

**Classes defined**: CairoOption

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 60
- Comment lines: 23
- Blank lines: -16

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
ts-node ts/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.ts
```

