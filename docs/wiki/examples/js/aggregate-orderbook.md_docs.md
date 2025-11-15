# Documentation: wiki/examples/js/aggregate-orderbook.md

## File Metadata

- **Path**: `wiki/examples/js/aggregate-orderbook.md`
- **Size**: 1,645 bytes
- **Lines**: 59
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Aggregate Orderbook](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

const aggregateOrderBookSide = function (orderbookSide, precision = undefined) {
    const result = []
    const amounts = {}
    for (let i = 0; i < orderbookSide.length; i++) {
        const ask = orderbookSide[i]
        let price = ask[0]
        if (precision !== undefined) {
            price = ccxt.decimalToPrecision (price, ccxt.ROUND, precision, ccxt.TICK_SIZE)
        }
        amounts[price] = (amounts[price] || 0) + ask[1]
    }
    Object.keys (amounts).forEach (price => {
        result.push ([
            parseFloat (price),
            amounts[price]
        ])
    })
    return result
}

const aggregateOrderBook = function (orderbook, precision = undefined) {
    let asks = aggregateOrderBookSide(orderbook['asks'], precision)
    let bids = aggregateOrderBookSide(orderbook['bids'], precision)
    return {
        'asks': ccxt.sortBy (asks, 0),
        'bids': ccxt.sortBy (bids, 0, true),
        'timestamp': orderbook['timestamp'],
        'datetime': orderbook['datetime'],
        'nonce': orderbook['nonce'],
    };
}

;(async () => {

    const exchange = new ccxt.coinbasepro()

    await exchange.loadMarkets ()

    // exchange.verbose = true // uncomment for verbose debug output

    // level 2 (default)
    const orderbook = await exchange.fetchOrderBook('BTC/USD')

    // or level 3
    // const orderbook = await exchange.fetchOrderBook('BTC/USD', undefined, { 'level': 3 })

    const step = 0.5 // 0.01, 0.1, 0.5, 1.0, 2.5, 5.0, 10.0
    console.log (aggregateOrderBook (orderbook, step))

})(); 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/aggregate-orderbook.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 41
- Comment lines: 4
- Blank lines: 14

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

**To execute this Markdown file:**

