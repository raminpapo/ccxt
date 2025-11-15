# Documentation: wiki/examples/js/advanced-error-handling.md

## File Metadata

- **Path**: `wiki/examples/js/advanced-error-handling.md`
- **Size**: 1,540 bytes
- **Lines**: 45
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Advanced Error Handling](./examples/js/)


 ```javascript
 "use strict";

const ccxt      = require ('../../ccxt.js');

// instantiate the exchange
let exchange = new ccxt.coinbasepro  ({
    'apiKey': 'XXXXXXXXXXXXXX',
    'secret': 'YYYYYYYYYYYYYY',
});

async function checkOrders(){
    try {
        // fetch orders
        let orders = await exchange.fetchOrders ('BTC/USDT');
        // output the result
        console.log (exchange.id, 'fetched orders', orders);
    } catch (e) {
        if (e instanceof ccxt.DDoSProtection || e.message.includes ('ECONNRESET')) {
            console.log ('[DDoS Protection] ' + e.message);
        } else if (e instanceof ccxt.RequestTimeout) {
            console.log ('[Request Timeout] ' + e.message);
        } else if (e instanceof ccxt.AuthenticationError) {
            console.log ('[Authentication Error] ' + e.message);
        } else if (e instanceof ccxt.ExchangeNotAvailable) {
            console.log ('[Exchange Not Available Error] ' + e.message);
        } else if (e instanceof ccxt.ExchangeError) {
            console.log ('[Exchange Error] ' + e.message);
        } else if (e instanceof ccxt.NetworkError) {
            console.log ('[Network Error] ' + e.message);
        } else {
            // you can throw it if you want to stop the execution
            // console.log ('[Exception ' + e.constructor.name + '] ' + e.message);
            throw e;
        }
    }
}

//  for demonstrational purposes, we use 1000 ms interval
setInterval(checkOrders, 1000); 
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/advanced-error-handling.md`.

**Functions defined**: checkOrders



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 32
- Comment lines: 6
- Blank lines: 7

### Main Components

**Functions** (1):
- `checkOrders()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

