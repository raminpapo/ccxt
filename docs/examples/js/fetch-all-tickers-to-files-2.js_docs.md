# Documentation: examples/js/fetch-all-tickers-to-files-2.js

## File Metadata

- **Path**: `examples/js/fetch-all-tickers-to-files-2.js`
- **Size**: 1,506 bytes
- **Lines**: 53
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
import { writeFileSync } from 'fs';
import path from 'path';

const enableRateLimit = true, exchanges = {}, tickers = {};


ccxt.exchanges.forEach (id => {
    try {
        const exchange = new ccxt[id] ()
        if (exchange.has['fetchTickers']) {
            exchanges[id] = exchange
        }
    } catch (e) {
        console.log ('Failed to initialize', id, e.constructor.name, e.message)
    }
})

async function main () {

    console.log ('Started')
    const start = Date.now ()

    try {
        const promises = Object.values (exchanges).map (exchange => (
            (async () => {
                console.log (exchange.id)
                try {
                    const response = await exchange.fetchTickers ()
                    tickers[exchange.id] = response
                } catch (e) {
                    console.log ('Failed to fetchTickers() from', exchange.id)
                }
            }) ()
        ))
        await Promise.all (promises)
    } catch (e) {
        console.log ('Failed awaiting all exchanges to complete')
    }

    Object.entries (tickers).forEach (([ id, response ]) => {
        const folder = 'C:/myproject/tickers'
        const filename = `${id}-tickers.json`
        console.log (path.join (folder, filename))
        writeFileSync (path.join (folder, filename), JSON.stringify (response))
    })

    const end = Date.now ()
    console.log (`Fetched tickers in ${(end - start) / 1000} seconds`)

}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/fetch-all-tickers-to-files-2.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 43
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
- `path` (imported)
- `fs` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/fetch-all-tickers-to-files-2.js
```

