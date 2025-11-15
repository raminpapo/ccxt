# Documentation: examples/py/coinbase-fetch-order.py

## File Metadata

- **Path**: `examples/py/coinbase-fetch-order.py`
- **Size**: 979 bytes
- **Lines**: 38
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402

# -----------------------------------------------------------------------------

print('CCXT Version:', ccxt.__version__)

# -----------------------------------------------------------------------------

exchange = ccxt.coinbase({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    # 'verbose': True,  # for debug output
})

order_id = '04204eaf-94d6-444a-b9b7-2f8a485311f6'
symbol = 'BTC/USDT'
since = None
limit = 3

try:
    fetch_order = exchange.fetch_order(order_id, symbol)
    # fetch_orders = exchange.fetch_orders(symbol, since, limit)
    # fetch_open_orders = exchange.fetch_open_orders(symbol, since, limit)
    pprint(fetch_order)
    # pprint(fetch_orders)
    # pprint(fetch_open_orders)
except Exception as err:
    print(err)

```

## High-Level Overview

This is a Python file located at `examples/py/coinbase-fetch-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 20
- Comment lines: 8
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
python examples/py/coinbase-fetch-order.py
```

