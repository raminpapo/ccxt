# Documentation: wiki/examples/js/okx-poll-fetch-my-trades.md

## File Metadata

- **Path**: `wiki/examples/js/okx-poll-fetch-my-trades.md`
- **Size**: 844 bytes
- **Lines**: 42
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Okx Poll Fetch My Trades](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js'

console.log ('CCXT Version:', ccxt.version)

async function main () {

    const exchange = new ccxt.okx ({

        // edit for your credentials
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET',
        'password': 'YOUR_API_PASSWORD',
    })

    await exchange.loadMarkets ()

    // if this script fails with a rate limiter error
    // uncomment the following line for debugging purposes

    // exchange.verbose = true

    while (true) {

        try {

            const trades = await exchange.fetchMyTrades ()
            console.log (new Date(), 'fetched', trades.length, 'trades')

        } catch (e) {

            console.log (e.constructor.name, e.message)
            break;
        }
    }
}

main () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/okx-poll-fetch-my-trades.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 23
- Comment lines: 4
- Blank lines: 15

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

