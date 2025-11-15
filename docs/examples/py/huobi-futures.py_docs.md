# Documentation: examples/py/huobi-futures.py

## File Metadata

- **Path**: `examples/py/huobi-futures.py`
- **Size**: 2,187 bytes
- **Lines**: 87
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
from random import randint
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.huobi({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'options': {
        'defaultType': 'future',
    },
})

markets = exchange.load_markets()


# exchange.verbose = True  # uncomment for debugging purposes if necessary

# creating and canceling a linear future (limit) order
symbol = 'ETH/USDT:USDT-220121' # the last segment is the date of expiration (can be next week, next quarter, ...) adjust it accordingly
order_type = 'limit'
side = 'buy'
offset = 'open'
leverage = 1
amount = 1
price = 1

params = {'offset': offset, 'lever_rate': leverage}

try:
    # fetching current balance
    balance = exchange.fetch_balance()
    print(balance)

    # placing an order
    order = exchange.create_order(symbol, order_type, side, amount, price, params)
    print(order)

    # listing open orders
    open_orders = exchange.fetch_open_orders(symbol)
    # print(open_orders)

    # canceling an order
    cancelOrder = exchange.cancel_order(order['id'], symbol)
    print(cancelOrder)
except Exception as e:
    print(type(e).__name__, str(e))


# creating and canceling a inverse future (limit) order
symbol = 'ADA/USD:ADA-220121' # the last segment is the date of expiration (can be next week, next quarter, ...) adjust it accordingly
order_type = 'limit'
side = 'buy'
offset = 'open'
leverage = 1
amount = 1 # 1 contract = 10 ADA
price = 1

params = {'offset': offset, 'lever_rate': leverage}

try:
    # fetching current balance
    balance = exchange.fetch_balance()
    # print(balance)

    # placing an order
    order = exchange.create_order(symbol, order_type, side, amount, price, params)
    print(order)

    # listing open orders
    open_orders = exchange.fetch_open_orders(symbol)
    # print(open_orders)

    # canceling an order
    cancelOrder = exchange.cancel_order(order['id'], symbol)
    print(cancelOrder)
except Exception as e:
    print(type(e).__name__, str(e))
```

## High-Level Overview

This is a Python file located at `examples/py/huobi-futures.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 50
- Comment lines: 15
- Blank lines: 22

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
python examples/py/huobi-futures.py
```

