# Documentation: wiki/examples/py/huobi-futures.md

## File Metadata

- **Path**: `wiki/examples/py/huobi-futures.md`
- **Size**: 2,122 bytes
- **Lines**: 90
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Huobi Futures](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
from random import randint
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/huobi-futures.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 90
- Code lines: 51
- Comment lines: 15
- Blank lines: 24

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

