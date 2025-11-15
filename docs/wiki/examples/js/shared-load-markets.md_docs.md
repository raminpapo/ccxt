# Documentation: wiki/examples/js/shared-load-markets.md

## File Metadata

- **Path**: `wiki/examples/js/shared-load-markets.md`
- **Size**: 3,161 bytes
- **Lines**: 86
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Shared Load Markets](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

// ----------------------------------------------------------------------------
// an example of how to load markets for each exchange just once
// in order to save memory and time for initializing multiple exchange instances
// see https://github.com/ccxt/ccxt/issues/7312 for details
// ----------------------------------------------------------------------------

const globalIds = [ 'binance', 'poloniex', 'bittrex', 'bitstamp' ]
const globalExchanges = {}

async function loadExchange (id) {
    try {
        const exchange = new ccxt[id] ()
        await exchange.loadMarkets ()
        globalExchanges[id] = exchange
    } catch (e) {
        // throw e // uncomment to break the entire program on any error
        // console.log (e) // print the exception and ignore this exchange
    }
}

async function main () {

    // initialize unique global exchange instances first
    await Promise.all (globalIds.map (async (id) => loadExchange (id)))
    console.log ('Loaded global exchanges:', Object.keys (globalExchanges))

    // load user exchanges and keys from a database or configure these via JSON
    const users = {
        'user1': {
            'binance': { 'apiKey': 'USER1_BINANCE_API_KEY', 'secret': 'USER1_BINANCE_SECRET' },
            'poloniex': { 'apiKey': 'USER1_POLONIEX_API_KEY', 'secret': 'USER1_POLONIEX_SECRET' }
        },
        'user2': {
            'poloniex': { 'apiKey': 'USER2_POLONIEX_API_KEY', 'secret': 'USER2_POLONIEX_SECRET' },
            'bittrex': { 'apiKey': 'USER2_BITTREX_API_KEY', 'secret': 'USER2_BITTREX_SECRET' }
        },
        'user3': {
            'bittrex': { 'apiKey': 'USER3_BITTREX_API_KEY', 'secret': 'USER3_BITTREX_SECRET' },
            'bitstamp': { 'apiKey': 'USER3_BITSTAMP_API_KEY', 'secret': 'USER3_BITSTAMP_SECRET' }
        }
    }

    // initialize local exchanges per user
    const localExchanges = {}
    for (const userId in users) {
        const userExchanges = {}
        for (const exchangeId in users[userId]) {
            if (exchangeId in globalExchanges) {
                const globalExchange = globalExchanges[exchangeId]
                const exchange = new ccxt[exchangeId] ({
                    // 'verbose': true, // uncomment for debug output
                    ... users[userId][exchangeId],
                });
                [
                    'ids',
                    'markets',
                    'markets_by_id',
                    'currencies',
                    'currencies_by_id',
                    'baseCurrencies',
                    'quoteCurrencies',
                    'symbols',
                ].forEach ((propertyName) => {
                    exchange[propertyName] = globalExchange[propertyName]
                })
                userExchanges[exchangeId] = exchange
            }
        }
        localExchanges[userId] = userExchanges
    }

    // print the loaded exchanges per user
    for (const userId in localExchanges) {
        console.log ('Loaded', userId, Object.keys (localExchanges[userId]))
    }
}

main ()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/shared-load-markets.md`.

**Functions defined**: main, loadExchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 86
- Code lines: 62
- Comment lines: 12
- Blank lines: 12

### Main Components

**Functions** (2):
- `loadExchange()`
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

