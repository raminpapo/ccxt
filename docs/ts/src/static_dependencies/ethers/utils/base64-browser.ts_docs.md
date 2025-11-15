# Documentation: ts/src/static_dependencies/ethers/utils/base64-browser.ts

## File Metadata

- **Path**: `ts/src/static_dependencies/ethers/utils/base64-browser.ts`
- **Size**: 622 bytes
- **Lines**: 26
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// utils/base64-browser

import { getBytes } from "./data.js";

import type { BytesLike } from "./data.js";


export function decodeBase64(textData: string): Uint8Array {
    textData = atob(textData);
    const data = new Uint8Array(textData.length);
    for (let i = 0; i < textData.length; i++) {
        data[i] = textData.charCodeAt(i);
    }
    return getBytes(data);
}

export function encodeBase64(_data: BytesLike): string {
    const data = getBytes(_data);
    let textData = "";
    for (let i = 0; i < data.length; i++) {
        textData += String.fromCharCode(data[i]);
    }
    return btoa(textData);
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/static_dependencies/ethers/utils/base64-browser.ts`.

**Functions defined**: decodeBase64, encodeBase64

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 18
- Comment lines: 1
- Blank lines: 7

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

**To execute this TypeScript file:**

```bash
ts-node ts/src/static_dependencies/ethers/utils/base64-browser.ts
```

