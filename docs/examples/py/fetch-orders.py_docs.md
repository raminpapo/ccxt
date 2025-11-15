# Documentation: examples/py/fetch-orders.py

## File Metadata

- **Path**: `examples/py/fetch-orders.py`
- **Size**: 422 bytes
- **Lines**: 22
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

exchange = ccxt.bittrex({
    "apiKey": "YOUR_API_KEY",
    "secret": "YOUR_API_SECRET",
    "enableRateLimit": True,
})

orders = exchange.fetch_orders()
print(orders)

order = exchange.fetch_order(orders[0]['id'])
print(order)

```

## High-Level Overview

This is a Python file located at `examples/py/fetch-orders.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 14
- Comment lines: 1
- Blank lines: 7

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
python examples/py/fetch-orders.py
```

