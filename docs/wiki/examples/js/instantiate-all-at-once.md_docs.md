# Documentation: wiki/examples/js/instantiate-all-at-once.md

## File Metadata

- **Path**: `wiki/examples/js/instantiate-all-at-once.md`
- **Size**: 1,135 bytes
- **Lines**: 52
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Instantiate All At Once](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

async function test () {

    let exchanges = { 
        "bittrex": {
            "apiKey": "YOUR_API_KEY", 
            "secret": "YOUR_SECRET",
        },
        "bitfinex": { 
            "apiKey": "YOUR_API_KEY", 
            "secret": "YOUR_SECRET"
        },
    }

    let ids = ccxt.exchanges.filter (id => id in exchanges)

    await Promise.all (ids.map (async id => {

        console.log (exchanges[id])

        // instantiate the exchange
        let exchange = new ccxt[id] (exchanges[id])
        console.log (exchange.id, exchange.apiKey)
        exchanges[id] = exchange

        // load markets
        await exchange.loadMarkets ()
        console.log (exchange.id, 'loaded')

        // check the balance
        if (exchange.apiKey) {
            let balance = await exchange.fetchBalance ()
            console.log (exchange.id, balance)
        }

        return exchange
    }))

    // when all of them are ready, do your other things
    console.log ('Loaded exchanges:', ids.join (', '))
}

test ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/instantiate-all-at-once.md`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 32
- Comment lines: 4
- Blank lines: 16

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
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

