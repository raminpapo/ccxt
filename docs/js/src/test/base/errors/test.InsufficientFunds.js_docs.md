# Documentation: js/src/test/base/errors/test.InsufficientFunds.js

## File Metadata

- **Path**: `js/src/test/base/errors/test.InsufficientFunds.js`
- **Size**: 2,613 bytes
- **Lines**: 64
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// ----------------------------------------------------------------------------
// @ts-nocheck
import assert from 'assert';
import ccxt from '../../../ccxt.js';
// ----------------------------------------------------------------------------
// will try to place a buy order at the minimum price level on minimum amount possible
// will skip if balance is positive or market limits are not set
export default async (exchange, symbol, balance) => {
    if (!exchange.has.createOrder) {
        console.log('createOrder() is not supported');
        return;
    }
    const markets = await exchange.loadMarkets();
    const market = markets[symbol];
    if (market.limits === undefined) {
        console.log('market.limits property is not set, will not test order creation');
        return;
    }
    const { price, amount, cost } = market.limits;
    if (price === undefined || amount === undefined || cost === undefined) {
        console.log('market.limits.[price|amount|cost] property is not set, will not test order creation');
        return;
    }
    let minPrice = price.min;
    let minAmount = amount.min; // will be adjusted co cover minCost if needed
    const minCost = cost.min;
    if (minPrice === undefined || minAmount === undefined || minCost === undefined) {
        console.log('min limits are not set, will not test order creation');
        return;
    }
    if (minCost > minPrice * minAmount) {
        minAmount = minCost / minPrice;
    }
    minPrice = exchange.priceToPrecision(symbol, minPrice);
    minAmount = exchange.amountToPrecision(symbol, minAmount);
    if (balance === undefined) {
        console.log('balance is not set, cannot ensure safety, will not test order creation');
        return;
    }
    // eslint-disable-next-line
    const { base, quote } = market;
    if (balance[quote] !== undefined && balance[quote].total > 0) {
        console.log('balance is not empty, will not test order creation');
        return;
    }
    try {
        console.log('creating limit buy order...', symbol, minAmount, minPrice);
        const order = await exchange.createLimitBuyOrder(symbol, minAmount, minPrice);
        console.log('order created although it should not had to - cleaning up');
        console.log(order);
        await exchange.cancelOrder(order.id, symbol);
        assert.fail();
    }
    catch (e) {
        if (e instanceof ccxt.InsufficientFunds) {
            console.log('InsufficientFunds thrown as expected');
        }
        else {
            console.log('InsufficientFunds failed, exception follows:');
            throw e;
        }
    }
};

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/base/errors/test.InsufficientFunds.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 57
- Comment lines: 6
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/base/errors/test.InsufficientFunds.js
```

