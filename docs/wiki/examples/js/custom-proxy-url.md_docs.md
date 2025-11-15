# Documentation: wiki/examples/js/custom-proxy-url.md

## File Metadata

- **Path**: `wiki/examples/js/custom-proxy-url.md`
- **Size**: 546 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Custom Proxy Url](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

(async function main () {

    const kraken1 = new ccxt.kraken ({
        proxy: function (url) {
            return 'https://example.com/?url=' + encodeURIComponent (url)
        },
    })

    console.log (await kraken1.loadMarkets ())

    const kraken2 = new ccxt.kraken ({
        proxy: function (url) {
            return 'https://cors-anywhere.herokuapp.com/' + url
        },
    })

    console.log (await kraken2.loadMarkets ())

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/custom-proxy-url.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 18
- Comment lines: 0
- Blank lines: 10

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

