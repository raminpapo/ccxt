# Documentation: examples/js/instantiate-all-at-once.js

## File Metadata

- **Path**: `examples/js/instantiate-all-at-once.js`
- **Size**: 1,068 bytes
- **Lines**: 47
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

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

## High-Level Overview

This is a JavaScript file located at `examples/js/instantiate-all-at-once.js`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 29
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
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/instantiate-all-at-once.js
```

