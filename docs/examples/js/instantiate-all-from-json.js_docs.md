# Documentation: examples/js/instantiate-all-from-json.js

## File Metadata

- **Path**: `examples/js/instantiate-all-from-json.js`
- **Size**: 766 bytes
- **Lines**: 32
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import settings from './credentials.json';

async function test () {

    const ids = ccxt.exchanges.filter (id => id in settings)

    const exchanges = ccxt.indexBy (await Promise.all (ids.map (async id => {

        // instantiate the exchange
        let exchange = new ccxt[id] (settings[id])

        // load markets
        await exchange.loadMarkets ()

        // check the balance
        if (exchange.apiKey) {
            let balance = await exchange.fetchBalance ()
            console.log (exchange.id, balance['free'])
        }

        return exchange
    })), 'id')

    // when all of them are ready, do your other things
    console.log ('Loaded exchanges:', Object.keys (exchanges).join (', '))
}

test ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/instantiate-all-from-json.js`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 16
- Comment lines: 4
- Blank lines: 12

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `./credentials.json` (imported)
- `../../js/ccxt.js` (referenced)
- `./credentials.json` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/instantiate-all-from-json.js
```

