# Documentation: js/src/static_dependencies/starknet/types/lib/contract/index.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/lib/contract/index.js`
- **Size**: 348 bytes
- **Lines**: 11
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// Basic elements
export var EntryPointType;
(function (EntryPointType) {
    EntryPointType["EXTERNAL"] = "EXTERNAL";
    EntryPointType["L1_HANDLER"] = "L1_HANDLER";
    EntryPointType["CONSTRUCTOR"] = "CONSTRUCTOR";
})(EntryPointType || (EntryPointType = {}));
export * from './abi.js';
export * from './legacy.js';
export * from './sierra.js';

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/types/lib/contract/index.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 11
- Code lines: 9
- Comment lines: 1
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./legacy.js` (imported)
- `./sierra.js` (imported)
- `./abi.js` (imported)
- `./legacy.js` (referenced)
- `./sierra.js` (referenced)
- `./abi.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/types/lib/contract/index.js
```

