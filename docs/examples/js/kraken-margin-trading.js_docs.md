# Documentation: examples/js/kraken-margin-trading.js

## File Metadata

- **Path**: `examples/js/kraken-margin-trading.js`
- **Size**: 2,937 bytes
- **Lines**: 89
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

console.log ('CCXT Version:', ccxt.version)

async function main () {

    const exchange = new ccxt.kraken ({
        "apiKey": "YOUR_API_KEY",
        "secret": "YOUR_SECRET",
    })

    console.log ('-----------------------------------------------------------')

    console.log ('Loading markets...')
    const markets = await exchange.loadMarkets ()
    console.log ('Markets loaded')

    // exchange.verbose = true // uncomment for debugging purposes

    try {

        const symbol = 'ETH/USDT'
            , market = exchange.market (symbol)
            , { base, quote } = market
            , type = 'market'
            , amount = market['limits']['amount']['min']
            , price = undefined
            , params = {
                'leverage': 2,
            }

        console.log ('-----------------------------------------------------------')

        // https://www.kraken.com/en-us/features/api#add-standard-order

        console.log ('Placing order...')
        let order = await exchange.createOrder (symbol, type, 'buy', amount, price, params)
        console.log ('Order placed:')
        console.log (order)

        console.log ('-----------------------------------------------------------')

        // https://www.kraken.com/en-us/features/api#get-open-positions

        console.log ('Fetching open positions...')
        const positionsParams = { 'docalcs': true }
        let openPositions = await exchange.fetchPositions (positionsParams)
        console.log ('Current positions:')
        console.log (openPositions)

        console.log ('-----------------------------------------------------------')

        console.log ('Fetching balance...')
        let balance = await exchange.fetchTotalBalance ()
        console.log ('Fetched balance:')
        console.log (base, balance[base], '(base)')
        console.log (quote, balance[quote], '(quote)')

        console.log ('-----------------------------------------------------------')

        console.log ('Closing the position...')
        order = await exchange.createOrder (symbol, type, 'sell', amount, price, params)
        console.log ('Got a response:')
        console.log (order)

        console.log ('-----------------------------------------------------------')

        console.log ('Fetching open positions again...')
        openPositions = await exchange.fetchPositions (positionsParams)
        console.log ('Current positions:')
        console.log (openPositions)

        console.log ('-----------------------------------------------------------')

        console.log ('Fetching balance...')
        balance = await exchange.fetchTotalBalance ()
        console.log ('Fetched balance:')
        console.log (base, balance[base], '(base)')
        console.log (quote, balance[quote], '(quote)')

    } catch (e) {

        console.log (e.constructor.name, e.message)
    }
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/kraken-margin-trading.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 89
- Code lines: 59
- Comment lines: 3
- Blank lines: 27

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

**To execute this JavaScript file:**

```bash
node examples/js/kraken-margin-trading.js
```

