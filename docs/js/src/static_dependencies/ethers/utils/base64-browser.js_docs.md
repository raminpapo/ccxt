# Documentation: js/src/static_dependencies/ethers/utils/base64-browser.js

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/base64-browser.js`
- **Size**: 533 bytes
- **Lines**: 19
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// utils/base64-browser
import { getBytes } from "./data.js";
export function decodeBase64(textData) {
    textData = atob(textData);
    const data = new Uint8Array(textData.length);
    for (let i = 0; i < textData.length; i++) {
        data[i] = textData.charCodeAt(i);
    }
    return getBytes(data);
}
export function encodeBase64(_data) {
    const data = getBytes(_data);
    let textData = "";
    for (let i = 0; i < data.length; i++) {
        textData += String.fromCharCode(data[i]);
    }
    return btoa(textData);
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/ethers/utils/base64-browser.js`.

**Functions defined**: decodeBase64, encodeBase64

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 17
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (2):
- `decodeBase64()`
- `encodeBase64()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./data.js` (imported)
- `./data.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/ethers/utils/base64-browser.js
```

