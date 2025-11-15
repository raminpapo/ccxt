# Documentation: ts/src/static_dependencies/node-fetch/errors/base.js

## File Metadata

- **Path**: `ts/src/static_dependencies/node-fetch/errors/base.js`
- **Size**: 346 bytes
- **Lines**: 18
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

This is a JavaScript file located at `ts/src/static_dependencies/node-fetch/errors/base.js`.

**Classes defined**: FetchBaseError



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 13
- Comment lines: 1
- Blank lines: 4

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
node ts/src/static_dependencies/node-fetch/errors/base.js
```

