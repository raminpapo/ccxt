# Documentation: examples/js/gateio-create-batch-order.js

## File Metadata

- **Path**: `examples/js/gateio-create-batch-order.js`
- **Size**: 1,003 bytes
- **Lines**: 43
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
const ccxt = require ('../../ccxt');

console.log ('CCXT Version:', ccxt.version);

async function main () {

    const exchange = new ccxt.gateio ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET',
    });
    await exchange.loadMarkets ();

    const ada = exchange.market ('ADA/USDT');
    const xrp = exchange.market ('XRP/USDT');

    const orders = await exchange.privateSpotPostBatchOrders (
        [
            {
                text: "t-123456",
                currency_pair: ada['id'],
                type: "limit",
                account: "spot",
                side: "buy",
                amount: "3",
                price: "0.4",
            },
            {
                text: "t-123456",
                currency_pair: xrp['id'],
                type: "limit",
                account: "spot",
                side: "buy",
                amount: "3",
                price: "0.47",
            },
        ]
    );

    console.log (orders);

};

main ();
```

## High-Level Overview

This is a JavaScript file located at `examples/js/gateio-create-batch-order.js`.

**Functions defined**: main



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 35
- Comment lines: 0
- Blank lines: 8

### Main Components

**Functions** (1):
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
node examples/js/gateio-create-batch-order.js
```

