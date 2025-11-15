# Documentation: wiki/examples/py/coinbase-create-order.md

## File Metadata

- **Path**: `wiki/examples/py/coinbase-create-order.md`
- **Size**: 756 bytes
- **Lines**: 37
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Create Order](./examples/py/)


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

symbol = 'BTC/USDT'
order_type = 'limit'
side = 'buy'
amount = 0.0003
order_price = 13500
stop_params = {
    'triggerPrice': 15000
}

try:
    limit_order = exchange.create_order(symbol, order_type, side, amount, order_price)
    # stop_order = exchange.create_order(symbol, order_type, side, amount, order_price, stop_params)
    pprint(limit_order)
    # pprint(stop_order)
except Exception as err:
    print(err)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinbase-create-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 25
- Comment lines: 4
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

