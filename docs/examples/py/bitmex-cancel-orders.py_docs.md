# Documentation: examples/py/bitmex-cancel-orders.py

## File Metadata

- **Path**: `examples/py/bitmex-cancel-orders.py`
- **Size**: 1,979 bytes
- **Lines**: 69
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


exchange = ccxt.bitmex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

# exchange.set_sandbox_mode(True)  # uncomment to use the testnet sandbox

symbol = 'BTC/USD'
type = 'limit'
side = 'buy'
amount = 100
price = 15000

### Creating multiple orders and cancel them
### https://github.com/ccxt/ccxt/issues/10112

## Example 1
## Canceling orders using ClientOrderId

# create first order
order1 = exchange.create_order(symbol, type, side, amount, price, {'clientOrderId': 'order0001'})
print(order1['id'])
# create second order
price = 10000
order2 = exchange.create_order(symbol, type, side, amount, price, {'clientOrderId': 'order0002'})
print(order2['id'])
# create third order
price = 9000
order3 = exchange.create_order(symbol, type, side, amount, price, {'clientOrderId': 'order0003'})
print(order3['id'])
# canceling first order
cancelResponse = exchange.cancel_order(None, None, {'clientOrderId': 'order0001'})
print(cancelResponse)
# cancel second and third order at the same time
cancelboth = exchange.cancel_orders(None, None, {'clientOrderId': ['order0002','order0003']})
print(cancelboth)

## Example 2
## Canceling orders using OrderId

# create first order
newOrder1 = exchange.create_order(symbol, type, side, amount, price)
print(newOrder1['id'])
# create second order
price = 10000
newOrder2 = exchange.create_order(symbol, type, side, amount, price)
print(newOrder2['id'])
# create third order
price = 9000
newOrder3 = exchange.create_order(symbol, type, side, amount, price)
print(newOrder3['id'])
# canceling first order
cancelResponse = exchange.cancel_order(newOrder1['id'])
print(cancelResponse)
# cancel second and third order at the same time
ids = [newOrder2['id'], newOrder3['id']]
cancelboth = exchange.cancel_orders(ids)
print(cancelboth)
```

## High-Level Overview

This is a Python file located at `examples/py/bitmex-cancel-orders.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 69
- Code lines: 39
- Comment lines: 18
- Blank lines: 12

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
python examples/py/bitmex-cancel-orders.py
```

