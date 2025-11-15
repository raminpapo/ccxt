# Documentation: wiki/examples/js/fetch-all-tickers-to-files.md

## File Metadata

- **Path**: `wiki/examples/js/fetch-all-tickers-to-files.md`
- **Size**: 2,454 bytes
- **Lines**: 83
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch All Tickers To Files](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import ololog from 'ololog';

const { noLocate } = ololog;
const log = noLocate;

import fs from 'fs';

// the numWorkers constant defines the number of concurrent workers
// those aren't really threads in terms of the async environment
// set this to the number of cores in your CPU * 2
// or play with this number to find a setting that works best for you

const numWorkers = 8;(async () => {

    // make an array of all exchanges
    const exchanges = ccxt.exchanges

        // filter coinmarketcap and theocean
        // coinmarketcap isn't really an exchange
        // theocean requires web3 dependencies to be installed

        .filter (id => ![ 'coinmarketcap', 'theocean' ].includes (id))

        // instantiate each exchange and save it to the exchanges list

        .map (id => new ccxt[id] ())

    // the worker function for each "async thread"
    const worker = async function () {

        // while the array of all exchanges is not empty
        while (exchanges.length > 0) {

            // pop one exchange from the array
            const exchange = exchanges.pop ()

            // check if it has the necessary method implemented
            if (exchange.has['fetchTickers']) {

                // try to do "the work" and handle errors if any
                try {

                    // fetch the response for all tickers from the exchange
                    const tickers = await exchange.fetchTickers ()

                    // make a filename from exchange id
                    const filename = exchange.id + '.json'

                    // save the response to a file
                    fs.writeFileSync (filename, JSON.stringify ({ tickers }));

                    // print out a message on success
                    log.green (exchange.id, 'tickers saved to', filename)

                } catch (e) {

                    // in case of error - print it out and ignore it further
                    log.red (e.constructor.name, e.message)
                }

            } else {

                log.red (exchange.id, "has['fetchTickers'] = false");
            }
        }
    }

    // create numWorkers "threads" (they aren't really threads)
    const workers = [ ... Array (numWorkers) ].map (_ => worker ())

    // wait for all of them to execute or fail
    await Promise.all (workers)

}) ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/fetch-all-tickers-to-files.md`.

**Functions defined**: for

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 83
- Code lines: 32
- Comment lines: 21
- Blank lines: 30

### Main Components

**Functions** (1):
- `for()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `ololog` (imported)
- `fs` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

