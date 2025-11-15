# Documentation: js/src/static_dependencies/node-fetch/utils/is-redirect.js

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/utils/is-redirect.js`
- **Size**: 231 bytes
- **Lines**: 11
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
const redirectStatus = new Set([301, 302, 303, 307, 308]);
/**
 * Redirect code matching
 *
 * @param {number} code - Status code
 * @return {boolean}
 */
export const isRedirect = code => {
    return redirectStatus.has(code);
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/node-fetch/utils/is-redirect.js`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 11
- Code lines: 10
- Comment lines: 6
- Blank lines: -5

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
node js/src/static_dependencies/node-fetch/utils/is-redirect.js
```

