# Documentation: js/src/static_dependencies/noble-hashes/cryptoNode.js

## File Metadata

- **Path**: `js/src/static_dependencies/noble-hashes/cryptoNode.js`
- **Size**: 135 bytes
- **Lines**: 3
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import * as nc from 'node:crypto';
export const crypto = nc && typeof nc === 'object' && 'webcrypto' in nc ? nc.webcrypto : undefined;

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/noble-hashes/cryptoNode.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 3
- Code lines: 2
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `node:crypto` (imported)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/noble-hashes/cryptoNode.js
```

