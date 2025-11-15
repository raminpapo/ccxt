# Documentation: wiki/examples/js/fetch-from-many-exchanges-simultaneously.md

## File Metadata

- **Path**: `wiki/examples/js/fetch-from-many-exchanges-simultaneously.md`
- **Size**: 514 bytes
- **Lines**: 26
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch From Many Exchanges Simultaneously](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import log from 'ololog';

const symbol = 'ETH/BTC'
const exchanges = [ 'coinbasepro', 'hitbtc2', 'poloniex' ]

;(async () => {

    const result = await Promise.all (exchanges.map (async id => {

        const exchange = new ccxt[id] ()
        const ticker = await exchange.fetchTicker (symbol)
        return exchange.extend ({ 'exchange': id }, ticker)

    }))

    log (result);

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/fetch-from-many-exchanges-simultaneously.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 15
- Comment lines: 0
- Blank lines: 11

### Main Components



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

