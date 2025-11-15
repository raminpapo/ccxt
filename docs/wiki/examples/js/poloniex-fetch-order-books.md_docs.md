# Documentation: wiki/examples/js/poloniex-fetch-order-books.md

## File Metadata

- **Path**: `wiki/examples/js/poloniex-fetch-order-books.md`
- **Size**: 966 bytes
- **Lines**: 41
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Poloniex Fetch Order Books](./examples/js/)


 ```javascript
 

// ----------------------------------------------------------------------------

import ccxt from '../../js/ccxt.js';

// ----------------------------------------------------------------------------

(async () => {

    const exchange = new ccxt.poloniex ({
        'verbose': process.argv.includes ('--verbose'),
        'timeout': 60000,
    })

    try {

        const response = await exchange.fetchOrderBooks ([
            'ETH/BTC',
            'LTC/BTC',
            'OMG/BTC',
        ])
        console.log (response);
        console.log ('Succeeded.')

    } catch (e) {

        console.log ('--------------------------------------------------------')
        console.log (e.constructor.name, e.message)
        console.log ('--------------------------------------------------------')
        console.log (exchange.last_http_response)
        console.log ('Failed.')
    }

}) ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/poloniex-fetch-order-books.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 25
- Comment lines: 2
- Blank lines: 14

### Main Components



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

