# Documentation: examples/py/wazirx-create-cancel-orders.py

## File Metadata

- **Path**: `examples/py/wazirx-create-cancel-orders.py`
- **Size**: 1,053 bytes
- **Lines**: 47
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

## High-Level Overview

This is a Python file located at `examples/py/wazirx-create-cancel-orders.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 28
- Comment lines: 6
- Blank lines: 13

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
python examples/py/wazirx-create-cancel-orders.py
```

