# Documentation: js/src/static_dependencies/node-fetch/utils/get-search.js

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/utils/get-search.js`
- **Size**: 316 bytes
- **Lines**: 9
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export const getSearch = parsedURL => {
    if (parsedURL.search) {
        return parsedURL.search;
    }
    const lastOffset = parsedURL.href.length - 1;
    const hash = parsedURL.hash || (parsedURL.href[lastOffset] === '#' ? '#' : '');
    return parsedURL.href[lastOffset - hash.length] === '?' ? '?' : '';
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/node-fetch/utils/get-search.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 9
- Code lines: 8
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
node js/src/static_dependencies/node-fetch/utils/get-search.js
```

