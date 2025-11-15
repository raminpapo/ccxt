# Documentation: examples/js/bybit-trailing.js

## File Metadata

- **Path**: `examples/js/bybit-trailing.js`
- **Size**: 1,837 bytes
- **Lines**: 62
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../ccxt');

console.log ('CCXT Version:', ccxt.version)

const exchange = new ccxt.bybit({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_KEY',
})

// exchange.set_sandbox_mode(true)  // enable sandbox mode

// Example 1 :: Swap : open position and set trailing stop and close it 
async function example1 () {
    exchange['options']['defaultType'] = 'swap'; // very important set swap as default type
    await exchange.loadMarkets ();

    const symbol = 'LTC/USDT:USDT';
    const market = exchange.market(symbol);
    
    // fetch swap balance
    const balance = await exchange.fetchBalance ();
    console.log (balance)

    // create order and open position
    const type = 'market';
    const side = 'buy';
    const amount = 0.1
    const price = undefined;
    const createOrder = await exchange.createOrder (symbol, type, side, amount, price);
    console.log ('Created order id:', createOrder['id'])

    // set trailing stop
    const rawSide = 'Buy'; // or 'Sell'
    const trailing_stop = 30; // YOUR TRAILING STOP HERE
    const trailingParams = {
        'symbol': market['id'],
        'side': rawSide,
        'trailing_stop': trailing_stop
    }
    const trailing_response = await exchange.privatePostPrivateLinearPositionTradingStop (trailingParams);
    console.log(trailing_response)

    // check opened position
    const symbols = [ symbol ];
    const positions = await exchange.fetchPositions (symbols);
    console.log (positions)

    // Close position by issuing a order in the opposite direction
    const params = {
        'reduce_only': true
    }
    const closePositionOrder = await exchange.createOrder (symbol, type, side, amount, price, params);
    console.log (closePositionOrder);
}

async function main () {
    await example1 ();
}

main ();
```

## High-Level Overview

This is a JavaScript file located at `examples/js/bybit-trailing.js`.

**Functions defined**: example1, main



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 42
- Comment lines: 7
- Blank lines: 13

### Main Components

**Functions** (2):
- `example1()`
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
node examples/js/bybit-trailing.js
```

