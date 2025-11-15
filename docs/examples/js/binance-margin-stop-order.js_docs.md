# Documentation: examples/js/binance-margin-stop-order.js

## File Metadata

- **Path**: `examples/js/binance-margin-stop-order.js`
- **Size**: 905 bytes
- **Lines**: 40
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';

console.log ('CCXT Version:', ccxt.version)

async function main () {

    const exchange = new ccxt.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET',
        'options': {
            'defaultType': 'margin',
        },
    })

    const markets = await exchange.loadMarkets ()

    exchange.verbose = true // uncomment for debugging purposes if necessary

    const symbol = 'BTC/USDT'
    const type = 'STOP_LOSS_LIMIT'
    const side = 'buy'
    const amount = YOUR_AMOUNT_HERE
    const price = YOUR_PRICE_HERE
    const params = {
        'stopPrice': YOUR_STOP_PRICE_HERE,
        'timeInForce': 'GTC',
    }

    try {
        const order = await exchange.createOrder (symbol, type, side, amount, price, params)
        console.log (order)
    } catch (e) {
        console.log (e.constructor.name, e.message)
    }
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/binance-margin-stop-order.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 29
- Comment lines: 0
- Blank lines: 11

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
node examples/js/binance-margin-stop-order.js
```

