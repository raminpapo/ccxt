# Documentation: examples/js/bitpanda-fetchMyTrades-reduce.js

## File Metadata

- **Path**: `examples/js/bitpanda-fetchMyTrades-reduce.js`
- **Size**: 1,634 bytes
- **Lines**: 36
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';

const bitpanda = new ccxt.bitpanda ({
    "apiKey": "INSERTYOURAPIKEY"
})


// output
`
fetching USDT/EUR trades on bitpanda
---------------------------------------------
maker volume 6621.81 USDT maker fee 5.62 USDT
taker volume 2544.82 USDT taker fee 3.27 USDT

sold 9166.63 USDT for 7802.38 EUR
bought 0.00 USDT for 0.00 EUR
`

;(async () => {
    const market = {
        symbol: 'USDT/EUR',
        base: 'USDT',
        quote: 'EUR',
    }
    console.log ('fetching', market.symbol, 'trades on bitpanda')
    console.log ('---------------------------------------------')
    const trades = await bitpanda.fetchMyTrades ('USDT/EUR')
    const makers = trades.filter (x => x.takerOrMaker === 'maker')
    const takers = trades.filter (x => x.takerOrMaker === 'taker')
    console.log ('maker volume', makers.reduce ((a, b) => a + b.amount, 0).toFixed (2), market.base, 'maker fee', makers.reduce ((a, b) => a + b.fee['cost'], 0).toFixed (2), market.base)
    console.log ('taker volume', takers.reduce ((a, b) => a + b.amount, 0).toFixed (2), market.base, 'taker fee', takers.reduce ((a, b) => a + b.fee['cost'], 0).toFixed (2), market.base)
    const sells = trades.filter (x => x.side === 'sell')
    const buys = trades.filter (x => x.side === 'buy')
    console.log ('\nsold', sells.reduce ((a, b) => a + b.amount, 0).toFixed (2), market.base, 'for', sells.reduce ((a, b) => a + b.cost, 0).toFixed (2), market.quote)
    console.log ('bought', buys.reduce ((a, b) => a + b.amount, 0).toFixed (2), market.base, 'for', buys.reduce ((a, b) => a + b.cost, 0).toFixed (2), market.quote)
}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/bitpanda-fetchMyTrades-reduce.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 30
- Comment lines: 1
- Blank lines: 5

### Main Components



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
node examples/js/bitpanda-fetchMyTrades-reduce.js
```

