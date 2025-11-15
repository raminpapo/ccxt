# Documentation: examples/js/bitrue-fetch-balance.js

## File Metadata

- **Path**: `examples/js/bitrue-fetch-balance.js`
- **Size**: 479 bytes
- **Lines**: 29
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

async function main () {

    console.log ('CCXT Version:', ccxt.version)

    const exchange = new ccxt.bitrue ({
        "apiKey": "YOUR_API_KEY",
        "secret": "YOUR_SECRET",
    })

    await exchange.loadMarkets ()

    exchange.verbose = true

    try {

        const balance = await exchange.fetchBalance ()
        console.log (balance)

    } catch (e) {
        console.log (e.constructor.name, e.message);
    }
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/bitrue-fetch-balance.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 17
- Comment lines: 0
- Blank lines: 12

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
node examples/js/bitrue-fetch-balance.js
```

