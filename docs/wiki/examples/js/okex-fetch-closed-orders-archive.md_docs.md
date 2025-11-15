# Documentation: wiki/examples/js/okex-fetch-closed-orders-archive.md

## File Metadata

- **Path**: `wiki/examples/js/okex-fetch-closed-orders-archive.md`
- **Size**: 698 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Okex Fetch Closed Orders Archive](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

console.log ('CCXT Version:', ccxt.version)

// https://github.com/ccxt/ccxt/issues/10179

async function main () {

    const exchange = new ccxt.okex ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'password': 'YOUR_PASSWORD',
        'options': {
            'fetchClosedOrders': {
                'method': 'privateGetTradeOrdersHistoryArchive'
            }
        }
    })

    const markets = await exchange.loadMarkets ()

    exchange.verbose = true

    const orders = await exchange.fetchClosedOrders ()
    console.log (orders)

}

main () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/okex-fetch-closed-orders-archive.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 22
- Comment lines: 1
- Blank lines: 13

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

