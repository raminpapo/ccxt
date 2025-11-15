# Documentation: examples/py/binance-batch-orders.py

## File Metadata

- **Path**: `examples/py/binance-batch-orders.py`
- **Size**: 667 bytes
- **Lines**: 34
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

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

## High-Level Overview

This is a Python file located at `examples/py/binance-batch-orders.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 23
- Comment lines: 1
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/binance-batch-orders.py
```

