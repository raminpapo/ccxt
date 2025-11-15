# Documentation: ts/src/static_dependencies/node-fetch/errors/fetch-error.js

## File Metadata

- **Path**: `ts/src/static_dependencies/node-fetch/errors/fetch-error.js`
- **Size**: 871 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript

import {FetchBaseError} from './base.js';

/**
 * @typedef {{ address?: string, code: string, dest?: string, errno: number, info?: object, message: string, path?: string, port?: number, syscall: string}} SystemError
*/

/**
 * FetchError interface for operational errors
 */
export class FetchError extends FetchBaseError {
	/**
	 * @param  {string} message -      Error message for human
	 * @param  {string} [type] -        Error type for machine
	 * @param  {SystemError} [systemError] - For Node.js system error
	 */
	constructor(message, type, systemError) {
		super(message, type);
		// When err.type is `system`, err.erroredSysCall contains system error and err.code contains system error code
		if (systemError) {
			// eslint-disable-next-line no-multi-assign
			this.code = this.errno = systemError.code;
			this.erroredSysCall = systemError.syscall;
		}
	}
}

```

## High-Level Overview

This is a JavaScript file located at `ts/src/static_dependencies/node-fetch/errors/fetch-error.js`.

**Classes defined**: FetchError

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 21
- Comment lines: 13
- Blank lines: -7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./base.js` (imported)
- `./base.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node ts/src/static_dependencies/node-fetch/errors/fetch-error.js
```

