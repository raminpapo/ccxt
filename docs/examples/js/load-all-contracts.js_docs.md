# Documentation: examples/js/load-all-contracts.js

## File Metadata

- **Path**: `examples/js/load-all-contracts.js`
- **Size**: 1,116 bytes
- **Lines**: 41
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
"use strict";

const ccxt = require ('../../js/ccxt.js')

console.log ('CCXT Version:', ccxt.version)

async function loadExchange (exchange) {
    try {
        await exchange.loadMarkets ()
        exchange.symbols.map (symbol => {
            const market = exchange.market (symbol)
            if (market['contract']) {
                console.log (exchange.id, 'loaded', market['type'], symbol, 'market')
            }
        })
    } catch (e) {
        console.log (e.constructor.name, e.message)
    }
}

async function loadAllExchanges (exchangeId) {
    try {

        const exchanges = [];
        [ 'swap', 'future', 'options' ].forEach (defaultType => {
            const exchange = new ccxt[exchangeId]()
            if (exchange.has[defaultType]) {
                exchanges.push (exchange);
            }
        })
        await Promise.all (exchanges.map (exchange => loadExchange (exchange)))
    } catch (e) {
        console.log (e.constructor.name, e.message)
    }
}

async function main () {
    await Promise.all (ccxt.exchanges.map (exchangeId => loadAllExchanges (exchangeId)))
}

main ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/load-all-contracts.js`.

**Functions defined**: main, loadAllExchanges, loadExchange



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 34
- Comment lines: 0
- Blank lines: 7

### Main Components

**Functions** (3):
- `loadAllExchanges()`
- `loadExchange()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/load-all-contracts.js
```

