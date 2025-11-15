# Documentation: examples/js/custom-proxy-url.js

## File Metadata

- **Path**: `examples/js/custom-proxy-url.js`
- **Size**: 486 bytes
- **Lines**: 23
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

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

## High-Level Overview

This is a JavaScript file located at `examples/js/custom-proxy-url.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 15
- Comment lines: 0
- Blank lines: 8

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

**To execute this JavaScript file:**

```bash
node examples/js/custom-proxy-url.js
```

