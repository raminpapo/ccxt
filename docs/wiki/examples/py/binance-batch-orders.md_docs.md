# Documentation: wiki/examples/py/binance-batch-orders.md

## File Metadata

- **Path**: `wiki/examples/py/binance-batch-orders.md`
- **Size**: 609 bytes
- **Lines**: 37
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Batch Orders](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.binance({
    "apiKey": "YOUR_API_KEY",
    "secret": "YOUR_SECRET",
})


orders = [
    {
        "symbol" : "BTCUSDT",
        "side" : "BUY",
        "positionSide" : "LONG",
        "type" : "MARKET",
        "quantity": float(0.005)
    }
]

orders = [exchange.encode_uri_component(exchange.json(order), safe=",") for order in orders]
response = exchange.fapiPrivatePostBatchOrders({
    'batchOrders': '[' + ','.join(orders) + ']'
})

print(response)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-batch-orders.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 24
- Comment lines: 1
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

