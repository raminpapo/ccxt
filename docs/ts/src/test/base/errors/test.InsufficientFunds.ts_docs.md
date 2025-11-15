# Documentation: ts/src/test/base/errors/test.InsufficientFunds.ts

## File Metadata

- **Path**: `ts/src/test/base/errors/test.InsufficientFunds.ts`
- **Size**: 2,621 bytes
- **Lines**: 65
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// ----------------------------------------------------------------------------
// @ts-nocheck
import assert from 'assert';
import ccxt from '../../../ccxt.js';

// ----------------------------------------------------------------------------
// will try to place a buy order at the minimum price level on minimum amount possible
// will skip if balance is positive or market limits are not set

export default async (exchange, symbol, balance) => {
    if (!exchange.has.createOrder) {
        console.log ('createOrder() is not supported');
        return;
    }
    const markets = await exchange.loadMarkets ();
    const market = markets[symbol];
    if (market.limits === undefined) {
        console.log ('market.limits property is not set, will not test order creation');
        return;
    }
    const { price, amount, cost } = market.limits;
    if (price === undefined || amount === undefined || cost === undefined) {
        console.log ('market.limits.[price|amount|cost] property is not set, will not test order creation');
        return;
    }
    let minPrice = price.min;
    let minAmount = amount.min; // will be adjusted co cover minCost if needed
    const minCost = cost.min;
    if (minPrice === undefined || minAmount === undefined || minCost === undefined) {
        console.log ('min limits are not set, will not test order creation');
        return;
    }
    if (minCost > minPrice * minAmount) {
        minAmount = minCost / minPrice;
    }
    minPrice = exchange.priceToPrecision (symbol, minPrice);
    minAmount = exchange.amountToPrecision (symbol, minAmount);
    if (balance === undefined) {
        console.log ('balance is not set, cannot ensure safety, will not test order creation');
        return;
    }
    // eslint-disable-next-line
    const { base, quote } = market;
    if (balance[quote] !== undefined && balance[quote].total > 0) {
        console.log ('balance is not empty, will not test order creation');
        return;
    }
    try {
        console.log ('creating limit buy order...', symbol, minAmount, minPrice);
        const order = await exchange.createLimitBuyOrder (symbol, minAmount, minPrice);
        console.log ('order created although it should not had to - cleaning up');
        console.log (order);
        await exchange.cancelOrder (order.id, symbol);
        assert.fail ();
    } catch (e) {
        if (e instanceof ccxt.InsufficientFunds) {
            console.log ('InsufficientFunds thrown as expected');
        } else {
            console.log ('InsufficientFunds failed, exception follows:');
            throw e;
        }
    }
};

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/errors/test.InsufficientFunds.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 55
- Comment lines: 6
- Blank lines: 4

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
npm test ts/src/test/base/errors/test.InsufficientFunds.ts
```

