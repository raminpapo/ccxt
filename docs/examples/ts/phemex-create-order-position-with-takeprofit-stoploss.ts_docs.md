# Documentation: examples/ts/phemex-create-order-position-with-takeprofit-stoploss.ts

## File Metadata

- **Path**: `examples/ts/phemex-create-order-position-with-takeprofit-stoploss.ts`
- **Size**: 2,224 bytes
- **Lines**: 63
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// @ts-nocheck
import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

// ------------------------------------------------------------------------------

async function example () {
    const exchange = new ccxt.phemex ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET',
    });

    const symbol = 'XRP/USDT:USDT';
    const side = 'buy'; // set it to 'buy' for a long position, 'sell' for a short position
    const order_type = 'limit'; // set it to 'market' or 'limit'
    const amount = 1; // how many contracts
    const price = 0.5; // set a price at your desired level

    // take profit and stop loss prices and types
    const take_profit_trigger_price = 0.6;
    const stop_loss_trigger_price = 0.4;
    const take_profit_limit_price = 0.7;
    const stop_loss_limit_price = 0.3;

    await exchange.loadMarkets ();

    // when symbol's price reaches your predefined "trigger price", stop-loss order would be activated as a "market order". but if you want it to be activated as a "limit order", then set a 'price' parameter for it
    const params = {
        'posSide': 'Long', // "Long" / "Short" for hedge mode
        'stopLoss': {
            'triggerPrice': stop_loss_trigger_price,
            'type': 'limit',
            'price': stop_loss_limit_price,
        },
        'takeProfit': {
            'triggerPrice': take_profit_trigger_price,
            'type': 'limit',
            'price': take_profit_limit_price,
        },
    };

    console.log ('-----------------------------------------------------------------------');

    // exchange.verbose = True  // uncomment for debugging purposes if necessary

    try {
        const created_order = await exchange.createOrder (symbol, order_type, side, amount, price, params);
        console.log ('Created an order', created_order);

        // Fetch all your open orders for this symbol
        const all_open_orders = await exchange.fetchOpenOrders (symbol);
        console.log ('Fetched all your orders for this symbol', all_open_orders);

        // To cancel a limit order, use "exchange.cancel_order(created_order['id'], symbol)""
    } catch (e) {
        console.log (e.toString ());
    }
}

await example ();


```

## High-Level Overview

This is a TypeScript file located at `examples/ts/phemex-create-order-position-with-takeprofit-stoploss.ts`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 40
- Comment lines: 8
- Blank lines: 15

### Main Components

**Functions** (1):
- `example()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node examples/ts/phemex-create-order-position-with-takeprofit-stoploss.ts
```

