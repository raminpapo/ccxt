# Documentation: examples/js/fetch-from-many-exchanges-simultaneously.js

## File Metadata

- **Path**: `examples/js/fetch-from-many-exchanges-simultaneously.js`
- **Size**: 430 bytes
- **Lines**: 21
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

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

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-from-many-exchanges-simultaneously.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 12
- Comment lines: 0
- Blank lines: 9

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

**To execute this JavaScript file:**

```bash
node examples/js/fetch-from-many-exchanges-simultaneously.js
```

