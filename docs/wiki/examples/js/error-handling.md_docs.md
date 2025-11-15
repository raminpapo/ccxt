# Documentation: wiki/examples/js/error-handling.md

## File Metadata

- **Path**: `wiki/examples/js/error-handling.md`
- **Size**: 2,477 bytes
- **Lines**: 94
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Error Handling](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

const verbose   = process.argv.includes ('--verbose');

//-----------------------------------------------------------------------------

const printSupportedExchanges = () => console.log ('Supported exchanges:', ccxt.exchanges.join (', '))

const printUsage = () => {
    console.log ('Usage: node', process.argv[1], 'id'.green)
    printSupportedExchanges ()
}

const run = async (id) => {

    // check if the exchange is supported by ccxt
    const exchangeFound = ccxt.exchanges.indexOf (id) > -1

    if (exchangeFound) {

        console.log ('Instantiating', id, 'exchange')

        // instantiate the exchange by id
        const exchange = new ccxt[id] ({ verbose })

        // try to load markets and catch the errors if any
        try {

            await exchange.loadMarkets ()

        } catch (e) {

            if (e instanceof ccxt.NetworkError) {
                console.log (exchange.id, 'loadMarkets failed due to a network error:', e.message)
            } else if (e instanceof ccxt.ExchangeError) {
                console.log (exchange.id, 'loadMarkets failed due to exchange error:', e.message)
            } else {
                console.log (exchange.id, 'loadMarkets failed with:', e.message)
            }

            // rethrow the error "higher up" the call chain
            throw e
        }

        // try to fetch a ticker and catch the errors if any
        try {

            const symbol = 'ETH/BTC'
            const response = await exchange.fetchTicker (symbol)
            console.log (response)

        } catch (e) {

            if (e instanceof ccxt.NetworkError) {
                console.log (exchange.id, 'fetchTicker failed due to a network error:', e.message)
            } else if (e instanceof ccxt.ExchangeError) {
                console.log (exchange.id, 'fetchTicker failed due to exchange error:', e.message)
            } else {
                console.log (exchange.id, 'fetchTicker failed with:', e.message)
            }

            // rethrow the error "higher up" the call chain
            throw e
        }

    } else {

        console.log ('Exchange', id, 'not found')
        printSupportedExchanges ()
    }
}

;(async function main () {

    if (process.argv.length > 2) {

        let id = process.argv[2]
        await run (id)

    } else {

        printUsage ()
    }

    process.exit ()

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/error-handling.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 94
- Code lines: 55
- Comment lines: 7
- Blank lines: 32

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

