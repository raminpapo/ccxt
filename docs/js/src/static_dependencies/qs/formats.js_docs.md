# Documentation: js/src/static_dependencies/qs/formats.js

## File Metadata

- **Path**: `js/src/static_dependencies/qs/formats.js`
- **Size**: 401 bytes
- **Lines**: 16
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
var replace = String.prototype.replace;
var percentTwenties = /%20/g;
var defaultFormat = 'RFC3986';
var formatters = {
    RFC1738: function (value) {
        return replace.call(value, percentTwenties, '+');
    },
    RFC3986: function (value) {
        return value;
    }
};
var RFC1738 = 'RFC1738';
var RFC3986 = 'RFC3986';
export default defaultFormat;
export { formatters, RFC1738, RFC3986 };

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/qs/formats.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 15
- Comment lines: 0
- Blank lines: 1

### Main Components

**Constants** (2):
- `RFC1738`
- `RFC3986`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/qs/formats.js
```

