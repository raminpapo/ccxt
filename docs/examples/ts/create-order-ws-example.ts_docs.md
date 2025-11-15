# Documentation: examples/ts/create-order-ws-example.ts

## File Metadata

- **Path**: `examples/ts/create-order-ws-example.ts`
- **Size**: 817 bytes
- **Lines**: 34
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const exchange = new ccxt.pro.binance ({
        'apiKey': 'MY_API_KEY',
        'secret': 'MY_SECRET',
    });
    exchange.setSandboxMode (true);
    exchange.verbose = true; // uncomment for debugging purposes if necessary
    // load markets
    await exchange.loadMarkets ();
    const symbol = 'ETH/USDT';
    const type = 'limit';
    const side = 'buy';
    const amount = 0.01;
    let price = 1000;
    let orders = [];
    for (let i=1; i<5; i++) {
        const response = await exchange.createOrderWs (
            symbol,
            type,
            side,
            amount,
            price
        );
        price += i;
        orders.push (response);
    }
    console.log (orders);
}
await example ();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/create-order-ws-example.ts`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 29
- Comment lines: 2
- Blank lines: 3

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
ts-node examples/ts/create-order-ws-example.ts
```

