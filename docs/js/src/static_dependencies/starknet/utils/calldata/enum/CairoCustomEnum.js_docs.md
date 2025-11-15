# Documentation: js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.js`
- **Size**: 1,854 bytes
- **Lines**: 52
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
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
     * @param enumContent an object with the variants as keys and the content as value. Only one content shall be defined.
     */
    constructor(enumContent) {
        const variantsList = Object.values(enumContent);
        if (variantsList.length === 0) {
            throw new Error('This Enum must have at least 1 variant');
        }
        const nbActiveVariants = variantsList.filter((content) => typeof content !== 'undefined').length;
        if (nbActiveVariants !== 1) {
            throw new Error('This Enum must have exactly one active variant');
        }
        this.variant = enumContent;
    }
    /**
     *
     * @returns the content of the valid variant of a Cairo custom Enum.
     */
    unwrap() {
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
    activeVariant() {
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

This is a JavaScript file located at `js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.js`.

**Classes defined**: CairoCustomEnum

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 51
- Comment lines: 22
- Blank lines: -21

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

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/utils/calldata/enum/CairoCustomEnum.js
```

