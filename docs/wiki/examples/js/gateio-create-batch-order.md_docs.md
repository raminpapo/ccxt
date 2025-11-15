# Documentation: wiki/examples/js/gateio-create-batch-order.md

## File Metadata

- **Path**: `wiki/examples/js/gateio-create-batch-order.md`
- **Size**: 1,072 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Gateio Create Batch Order](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/gateio-create-batch-order.md`.

**Functions defined**: main



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 38
- Comment lines: 0
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

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

