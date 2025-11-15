# Documentation: wiki/examples/py/kucoin-fetch-closed-orders-pagination.md

## File Metadata

- **Path**: `wiki/examples/py/kucoin-fetch-closed-orders-pagination.md`
- **Size**: 759 bytes
- **Lines**: 37
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Kucoin Fetch Closed Orders Pagination](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/kucoin-fetch-closed-orders-pagination.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 26
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

**To execute this Markdown file:**

