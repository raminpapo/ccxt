# Documentation: wiki/examples/py/wazirx-create-cancel-orders.md

## File Metadata

- **Path**: `wiki/examples/py/wazirx-create-cancel-orders.md`
- **Size**: 1,002 bytes
- **Lines**: 50
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Wazirx Create Cancel Orders](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.wazirx({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'options': {
        'defaultType': 'swap',
    },
})

markets = exchange.load_markets()

symbol = 'LTC/USDT'
amount = 0.1
price = 20

# Opening limit order
order = exchange.create_order(symbol, 'limit', 'buy', amount, price)
pprint(order)

# Opening stop-limit order
order2 = exchange.create_order(symbol, 'limit', 'buy', amount, price, {"stopPrice": 70})
pprint(order2)

# Opening second limit order
order3 = exchange.create_order(symbol, 'limit', 'buy', amount, price)
pprint(order3)

# Canceling first limit order
response = exchange.cancel_order(order['id'], symbol)
print(response)

# Canceling all open orders (second and third order)
response = exchange.cancel_all_orders(symbol)
print(response) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/wazirx-create-cancel-orders.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 29
- Comment lines: 6
- Blank lines: 15

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

