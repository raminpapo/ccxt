# Documentation: wiki/examples/js/theocean.md

## File Metadata

- **Path**: `wiki/examples/js/theocean.md`
- **Size**: 1,269 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Theocean](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/theocean.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 30
- Comment lines: 5
- Blank lines: 12

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

**To execute this Markdown file:**

