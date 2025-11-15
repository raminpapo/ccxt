# Documentation: wiki/examples/js/instantiate-all-from-json.md

## File Metadata

- **Path**: `wiki/examples/js/instantiate-all-from-json.md`
- **Size**: 835 bytes
- **Lines**: 37
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Instantiate All From Json](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/instantiate-all-from-json.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 19
- Comment lines: 4
- Blank lines: 14

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

**To execute this Markdown file:**

