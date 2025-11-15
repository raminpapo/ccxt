# Documentation: wiki/examples/js/coinone-markets.md

## File Metadata

- **Path**: `wiki/examples/js/coinone-markets.md`
- **Size**: 412 bytes
- **Lines**: 22
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinone Markets](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/coinone-markets.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 13
- Comment lines: 0
- Blank lines: 9

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

**To execute this Markdown file:**

