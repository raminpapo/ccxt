# Documentation: js/src/static_dependencies/node-fetch/errors/base.js

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/errors/base.js`
- **Size**: 397 bytes
- **Lines**: 15
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export class FetchBaseError extends Error {
    constructor(message, type) {
        super(message);
        // Hide custom error implementation details from end-users
        Error.captureStackTrace(this, this.constructor);
        this.type = type;
    }
    get name() {
        return this.constructor.name;
    }
    get [Symbol.toStringTag]() {
        return this.constructor.name;
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/node-fetch/errors/base.js`.

**Classes defined**: FetchBaseError



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 13
- Comment lines: 1
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
node js/src/static_dependencies/node-fetch/errors/base.js
```

