# Documentation: examples/js/coinex-futures.js

## File Metadata

- **Path**: `examples/js/coinex-futures.js`
- **Size**: 2,461 bytes
- **Lines**: 75
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../ccxt');

console.log ('CCXT Version:', ccxt.version)

let exchange = new ccxt.coinex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
})

// Example 1 :: Swap : fetch balance, create a limit swap order with leverage
async function example1 () {
    exchange['options']['defaultType'] = 'swap';
    exchange.options['defaultMarginMode'] = 'cross' // or isolated
    await exchange.loadMarkets ();

    const symbol = 'ADA/USDT:USDT';

    // fetchBalance
    const balance = await exchange.fetchBalance ();
    console.log (balance)

    // set the desired leverage (has to be made before placing the order and for a specific symbol)
    const leverage = 8;
    const leverage_response = await exchange.setLeverage(leverage, symbol)

    // create limit order
    const amount = 50;
    const price = 0.3 // adjust this accordingly
    const createOrder = await exchange.createOrder (symbol, 'limit', 'buy', amount, price);
    console.log ('Created order id:', createOrder['id'])
}

// Example 2 :: Swap :: open a position and close it
async function example2 () {
    exchange['options']['defaultType'] = 'swap';
    exchange.options['defaultMarginMode'] = 'cross' // or isolated
    await exchange.loadMarkets ();

    const symbol = 'ADA/USDT:USDT';

    // fetchBalance
    const balance = await exchange.fetchBalance ();
    console.log (balance)

    // set the desired leverage (has to be made before placing the order and for a specific symbol)
    const leverage = 8;
    const leverage_response = await exchange.setLeverage(leverage, symbol)

    // create market order and open position
    const amount = 50;
    const createOrder = await exchange.createOrder (symbol, 'market', 'buy', amount);
    console.log ('Created order id:', createOrder['id'])

    // check if the order was filled and the position opened
    const position = await exchange.fetchPositions (symbol);
    console.log (position)

    // close position (assuming it was already opened) by issuing an order in the opposite direction
    const params = {
        'reduce_only': true
    }
    const closePositionOrder = await exchange.createOrder (symbol, 'market', 'sell', amount, undefined, params);
    console.log (closePositionOrder);
}

// -----------------------------------------------------------------------------------------

async function main () {
    await example1 ();
    await example2 ();
}

main ();
```

## High-Level Overview

This is a JavaScript file located at `examples/js/coinex-futures.js`.

**Functions defined**: example2, example1, main



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 46
- Comment lines: 11
- Blank lines: 18

### Main Components

**Functions** (3):
- `example1()`
- `example2()`
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/coinex-futures.js
```

