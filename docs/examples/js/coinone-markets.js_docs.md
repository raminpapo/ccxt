# Documentation: examples/js/coinone-markets.js

## File Metadata

- **Path**: `examples/js/coinone-markets.js`
- **Size**: 353 bytes
- **Lines**: 17
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import log from 'ololog';
import ccxt from '../../js/ccxt.js';

const exchange = new ccxt.coinone ({
    'verbose': process.argv.includes ('--verbose'),
})

;(async function main () {

    const markets = await exchange.loadMarkets ()
    log (markets)
    log ('\n' + exchange['name'] + ' supports ' + Object.keys (markets).length + ' pairs')

}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/coinone-markets.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 10
- Comment lines: 0
- Blank lines: 7

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
- `ololog` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/coinone-markets.js
```

