# Documentation: js/src/static_dependencies/noble-hashes/crypto.js

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/crypto.js`
- **Size**: 112 bytes
- **Lines**: 2
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export const crypto = typeof globalThis === 'object' && 'crypto' in globalThis ? globalThis.crypto : undefined;

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/noble-hashes/crypto.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 2
- Code lines: 1
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/noble-hashes/crypto.js
```

