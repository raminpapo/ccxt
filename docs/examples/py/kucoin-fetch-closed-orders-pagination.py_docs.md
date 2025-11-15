# Documentation: examples/py/kucoin-fetch-closed-orders-pagination.py

## File Metadata

- **Path**: `examples/py/kucoin-fetch-closed-orders-pagination.py`
- **Size**: 800 bytes
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

exchange = ccxt.kucoin({
    "apiKey": "YOUR_API_KEY",
    "secret": "YOUR_SECRET",
    "password": "YOUR_PASSWORD"
})

symbol = 'ETH/USDT'
now = exchange.milliseconds()
day = 24 * 3600 * 1000
week = 7 * day
since = now - 365 * day  # start one year back
limit = 20

while since < now:

    end = min(since + week, now)
    params = {'endAt': end}
    orders = exchange.fetch_closed_orders(symbol, since, limit, params)
    print(exchange.iso8601(since), '-', exchange.iso8601(end), len(orders), 'orders')
    if len(orders) == limit:
        since = orders[-1]['timestamp']
    else:
        since += week

```

## High-Level Overview

This is a Python file located at `examples/py/kucoin-fetch-closed-orders-pagination.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 25
- Comment lines: 1
- Blank lines: 8

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
python examples/py/kucoin-fetch-closed-orders-pagination.py
```

