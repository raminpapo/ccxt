# Documentation: wiki/examples/py/coinbase-fetch-order.md

## File Metadata

- **Path**: `wiki/examples/py/coinbase-fetch-order.md`
- **Size**: 757 bytes
- **Lines**: 35
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Fetch Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)
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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinbase-fetch-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 21
- Comment lines: 6
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

