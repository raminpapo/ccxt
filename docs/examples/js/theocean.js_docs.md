# Documentation: examples/js/theocean.js

## File Metadata

- **Path**: `examples/js/theocean.js`
- **Size**: 1,217 bytes
- **Lines**: 42
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
(async function main () {
    const walletAddress = process.env['WALLET_ADDRESS']
    const privateKey = process.env['PRIVATE_KEY']
    const apiKey = process.env['API_KEY']
    const secret = process.env['SECRET']

    const ocean = new ccxt.theocean({
        walletAddress,
        privateKey,
        apiKey,
        secret
    });

    // get balance
    const balance = await ocean.fetchBalanceByCode('REP');
    console.log('REP balance: ', balance);

    // get order book
    const orderBook = await ocean.fetchOrderBook('REP/ZRX');
    console.log('REP/ZRX orderbook: ', orderBook);

    // placing order
    const placeResult = await ocean.createOrder('REP/ZRX', 'limit', 'sell', '0.5', '30');
    const id = placeResult['id'];
    console.log('result of placing order: ', placeResult);

    // cancel order
    if (placeResult['remaining'] > 0) {
        const cancelResult = await ocean.cancelOrder(id);
        console.log('cancel result: ', cancelResult);
    }

    // cancel all open user orders
    const cancelAllOrderssResult = await ocean.cancelAllOrders();
    console.log('cancel all orders result: ', cancelAllOrderssResult);

    process.exit ();
}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/theocean.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 27
- Comment lines: 5
- Blank lines: 10

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
node examples/js/theocean.js
```

