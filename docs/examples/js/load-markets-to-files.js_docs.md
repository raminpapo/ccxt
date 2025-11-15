# Documentation: examples/js/load-markets-to-files.js

## File Metadata

- **Path**: `examples/js/load-markets-to-files.js`
- **Size**: 2,164 bytes
- **Lines**: 58
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import path from 'path';
import fs from 'fs';

const enableRateLimit = true,
      // exchange defaults
      // ------------------------------------------------------------------------
      // path to your folder, for example '/myproject/markets' or 'C:/myproject/markets'
      options = { enableRateLimit },
      // writes to current working directory if left empty
      // ------------------------------------------------------------------------
      // use a reasonable value for maxConcurrency to avoid network congestion
      // a burst of requests in a short period of time will cause
      // excessive competition for networking resources within the application
      folder = '',
      maxConcurrency = 7;

async function main () {

    const allExchanges = ccxt.exchanges.map (id => {
            try {
                return new ccxt[id] (options)
            } catch (e) {
                console.log ('Failed to initialize', id, e.constructor.name)
            }
        }).filter (x => x)
        , allExchangesByIds = ccxt.indexBy (allExchanges, 'id')
        , exchangeIds = Object.keys (allExchangesByIds)

    const load = async () => {
        while (exchangeIds.length > 0) {
            const id = exchangeIds.pop ()
            const exchange = allExchangesByIds[id]
            const file = path.join (folder, `saved-markets-${exchange.id}.json`)
            try {
                await exchange.loadMarkets ()
                const { id, markets } = exchange
                await writeFile (file, JSON.stringify ({ id, markets }))
                console.log ('Loaded markets from', id, 'to', file)
            } catch (e) {
                console.log ('Failed to load markets from', id, 'to', file, e.constructor.name)
            }
        }
    }

    const started = ccxt.milliseconds ()
    const loaders = Array (maxConcurrency).fill ().map (x => load ())
    await Promise.all (loaders)
    const stopped  = ccxt.milliseconds ()
    console.log ('Done loading', allExchanges.length, 'exchanges in', ((stopped - started) / 1000).toFixed (2), 'seconds')

    // other code...
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/load-markets-to-files.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 39
- Comment lines: 9
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
node examples/js/load-markets-to-files.js
```

