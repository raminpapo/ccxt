# Documentation: js/src/pro/coinbaseadvanced.js

## File Metadata

- **Path**: `js/src/pro/coinbaseadvanced.js`
- **Size**: 447 bytes
- **Lines**: 13
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// ---------------------------------------------------------------------------
import coinbase from './coinbase.js';
// ---------------------------------------------------------------------------
export default class coinbaseadvanced extends coinbase {
    describe() {
        return this.deepExtend(super.describe(), {
            'id': 'coinbaseadvanced',
            'name': 'Coinbase Advanced',
            'alias': true,
        });
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/coinbaseadvanced.js`.

**Classes defined**: coinbaseadvanced

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 13
- Code lines: 10
- Comment lines: 2
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./coinbase.js` (imported)
- `./coinbase.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/pro/coinbaseadvanced.js
```

