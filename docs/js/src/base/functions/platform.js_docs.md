# Documentation: js/src/base/functions/platform.js

## File Metadata

- **Path**: `js/src/base/functions/platform.js`
- **Size**: 1,340 bytes
- **Lines**: 22
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// @ts-nocheck
// ----------------------------------------------------------------------------
// There's been a lot of messing with this code...
// The problem is to satisfy the following requirements:
// - properly detect isNode == true on server side and isNode == false in the browser (on client side)
// - make sure create-react-app, react-starter-kit and other react frameworks work
// - make sure it does not break the browserified version (when linked into a html from a cdn)
// - make sure it does not break the webpacking and babel-transpiled scripts
// - make sure it works in Electron
// - make sure it works with Angular.js
// - make sure it does not break other possible usage scenarios
const isBrowser = typeof window !== 'undefined';
const isElectron = typeof process !== 'undefined' &&
    typeof process.versions !== 'undefined' &&
    typeof process.versions.electron !== 'undefined';
const isWebWorker = typeof WorkerGlobalScope !== 'undefined' && (self instanceof WorkerGlobalScope);
const isWindows = typeof process !== 'undefined' && process.platform === "win32";
const isDeno = typeof Deno !== 'undefined';
const isNode = !(isBrowser || isWebWorker || isDeno);
// ----------------------------------------------------------------------------
export { isBrowser, isElectron, isWebWorker, isNode, isDeno, isWindows, };

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/functions/platform.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 9
- Comment lines: 12
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
node js/src/base/functions/platform.js
```

