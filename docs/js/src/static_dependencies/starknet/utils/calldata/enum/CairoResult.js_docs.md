# Documentation: js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.js`
- **Size**: 1,687 bytes
- **Lines**: 58
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export var CairoResultVariant;
(function (CairoResultVariant) {
    CairoResultVariant[CairoResultVariant["Ok"] = 0] = "Ok";
    CairoResultVariant[CairoResultVariant["Err"] = 1] = "Err";
})(CairoResultVariant || (CairoResultVariant = {}));
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
export class CairoResult {
    constructor(variant, resultContent) {
        if (!(variant in CairoResultVariant)) {
            throw new Error('Wrong variant : should be CairoResultVariant.Ok or .Err.');
        }
        if (variant === CairoResultVariant.Ok) {
            this.Ok = resultContent;
            this.Err = undefined;
        }
        else {
            this.Ok = undefined;
            this.Err = resultContent;
        }
    }
    /**
     *
     * @returns the content of the valid variant of a Cairo Result.
     */
    unwrap() {
        if (typeof this.Ok !== 'undefined') {
            return this.Ok;
        }
        if (typeof this.Err !== 'undefined') {
            return this.Err;
        }
        throw new Error('Both Result.Ok and .Err are undefined. Not authorized.');
    }
    /**
     *
     * @returns true if the valid variant is 'Ok'.
     */
    isOk() {
        return !(typeof this.Ok === 'undefined');
    }
    /**
     *
     * @returns true if the valid variant is 'isErr'.
     */
    isErr() {
        return !(typeof this.Err === 'undefined');
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.js`.

**Classes defined**: CairoResult

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 57
- Comment lines: 22
- Blank lines: -21

### Main Components

**Classes** (1):
- `CairoResult`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/calldata/enum/CairoResult.js
```

