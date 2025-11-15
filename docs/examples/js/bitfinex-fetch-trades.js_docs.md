# Documentation: examples/js/bitfinex-fetch-trades.js

## File Metadata

- **Path**: `examples/js/bitfinex-fetch-trades.js`
- **Size**: 1,081 bytes
- **Lines**: 35
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


// ----------------------------------------------------------------------------

import ccxt from '../../js/ccxt.js';
import log from 'ololog';
import asTable from 'as-table';

// ----------------------------------------------------------------------------

const // ----------------------------------------------------------------------------
table = asTable.configure ({ delimiter: ' | ' });(async () => {

    const exchange = new ccxt.bitfinex ({
        'verbose': process.argv.includes ('--verbose'),
        'timeout': 60000,
    })

    try {

        const response = await exchange.fetchTrades ('ETH/BTC', 1518983548636 - 2 * 24 * 60 * 60 * 1000)
        log (table (response))
        log (response.length.toString (), 'trades')
        log.green ('Succeeded.')

    } catch (e) {

        log.dim ('--------------------------------------------------------')
        log (e.constructor.name, e.message)
        log.dim ('--------------------------------------------------------')
        log.dim (exchange.last_http_response)
        log.error ('Failed.')
    }

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/bitfinex-fetch-trades.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 22
- Comment lines: 2
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
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/bitfinex-fetch-trades.js
```

