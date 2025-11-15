# Documentation: examples/js/market-status-and-currency-status.js

## File Metadata

- **Path**: `examples/js/market-status-and-currency-status.js`
- **Size**: 709 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import log from 'ololog';
import asTable from 'as-table';

(async function main () {

    let kraken = new ccxt.kraken ()
    await kraken.loadMarkets ()

    const markets = Object.values (kraken.markets).map (market => ({
        symbol: market.symbol,
        active: market.active,
    }))

    log.bright.green.noLocate ('Markets:')
    log.green.noLocate (asTable (markets), '\n')

    const currencies = Object.values (kraken.currencies).map (currency => ({
        code: currency.code,
        active: currency.active,
        status: currency.status,
    }))

    log.bright.yellow.noLocate ('Currencies:')
    log.yellow.noLocate (asTable (currencies))

}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/market-status-and-currency-status.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 20
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
- `ololog` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/market-status-and-currency-status.js
```

