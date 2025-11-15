# Documentation: examples/js/sample-local-proxy-server-with-cors.js

## File Metadata

- **Path**: `examples/js/sample-local-proxy-server-with-cors.js`
- **Size**: 623 bytes
- **Lines**: 13
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// @ts-nocheck
// JavaScript sample Proxy with CORS support
// Save this in a file like cors.js and run with:
//    node cors [port]
// It will listen for your requests on the port you pass in command line (or port 8080 by default)
import cors from 'cors-anywhere'; // npm install cors-anywhere
const port = (process.argv.length > 2) ? parseInt(process.argv[2]) : 8080; // if not provided from cli, default to 8080
cors.createServer({
// you can set origin, if needed by exchange
// setHeaders: { 'origin': 'https://www.bitmex.com' }
}).listen(port, 'localhost');
console.log('Running CORS Anywhere on localhost:' + port);

```

## High-Level Overview

This is a JavaScript file located at `examples/js/sample-local-proxy-server-with-cors.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 5
- Comment lines: 7
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `cors-anywhere` (imported)
- `https://www.bitmex.com` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/sample-local-proxy-server-with-cors.js
```

