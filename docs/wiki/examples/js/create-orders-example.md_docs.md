# Documentation: wiki/examples/js/create-orders-example.md

## File Metadata

- **Path**: `wiki/examples/js/create-orders-example.md`
- **Size**: 694 bytes
- **Lines**: 23
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Create Orders Example](./examples/js/)


 ```javascript
 import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
async function example() {
    const exchange = new ccxt.binance({
        'apiKey': 'MY_API_KEY',
        'secret': 'MY_SECRET',
    });
    exchange.setSandboxMode(true);
    await exchange.loadMarkets();
    exchange.verbose = true; // uncomment for debugging purposes if necessary
    const orders = await exchange.createOrders([
        { 'symbol': 'LTC/USDT:USDT', 'type': 'limit', 'side': 'buy', 'amount': 10, 'price': 55 },
        { 'symbol': 'ETH/USDT:USDT', 'type': 'market', 'side': 'buy', 'amount': 0.5 },
    ]);
    console.log(orders);
}
await example();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/create-orders-example.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 19
- Comment lines: 1
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

**To execute this Markdown file:**

