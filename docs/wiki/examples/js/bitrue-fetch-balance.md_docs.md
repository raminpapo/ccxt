# Documentation: wiki/examples/js/bitrue-fetch-balance.md

## File Metadata

- **Path**: `wiki/examples/js/bitrue-fetch-balance.md`
- **Size**: 543 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitrue Fetch Balance](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/bitrue-fetch-balance.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 20
- Comment lines: 0
- Blank lines: 14

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

