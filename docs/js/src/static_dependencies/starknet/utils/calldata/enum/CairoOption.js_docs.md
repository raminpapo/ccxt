# Documentation: js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.js`
- **Size**: 1,732 bytes
- **Lines**: 59
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export var CairoOptionVariant;
(function (CairoOptionVariant) {
    CairoOptionVariant[CairoOptionVariant["Some"] = 0] = "Some";
    CairoOptionVariant[CairoOptionVariant["None"] = 1] = "None";
})(CairoOptionVariant || (CairoOptionVariant = {}));
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
export class CairoOption {
    constructor(variant, someContent) {
        if (!(variant in CairoOptionVariant)) {
            throw new Error('Wrong variant : should be CairoOptionVariant.Some or .None.');
        }
        if (variant === CairoOptionVariant.Some) {
            if (typeof someContent === 'undefined') {
                throw new Error('The creation of a Cairo Option with "Some" variant needs a content as input.');
            }
            this.Some = someContent;
            this.None = undefined;
        }
        else {
            this.Some = undefined;
            this.None = true;
        }
    }
    /**
     *
     * @returns the content of the valid variant of a Cairo custom Enum.
     *  If None, returns 'undefined'.
     */
    unwrap() {
        if (this.None) {
            return undefined;
        }
        return this.Some;
    }
    /**
     *
     * @returns true if the valid variant is 'isSome'.
     */
    isSome() {
        return !(typeof this.Some === 'undefined');
    }
    /**
     *
     * @returns true if the valid variant is 'isNone'.
     */
    isNone() {
        return this.None === true;
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.js`.

**Classes defined**: CairoOption

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 58
- Comment lines: 23
- Blank lines: -22

### Main Components

**Classes** (1):
- `CairoOption`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/calldata/enum/CairoOption.js
```

