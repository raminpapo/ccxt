# Documentation: wiki/examples/js/load-all-contracts.md

## File Metadata

- **Path**: `wiki/examples/js/load-all-contracts.md`
- **Size**: 1,178 bytes
- **Lines**: 46
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Load All Contracts](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/load-all-contracts.md`.

**Functions defined**: main, loadAllExchanges, loadExchange



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 37
- Comment lines: 0
- Blank lines: 9

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

**To execute this Markdown file:**

