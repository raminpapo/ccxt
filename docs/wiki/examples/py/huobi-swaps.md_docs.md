# Documentation: wiki/examples/py/huobi-swaps.md

## File Metadata

- **Path**: `wiki/examples/py/huobi-swaps.md`
- **Size**: 1,879 bytes
- **Lines**: 92
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Huobi Swaps](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
from random import randint
import sys
from pprint import pprint


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.huobi({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
    'options': {
        'defaultType': 'swap',
    },
})

markets = exchange.load_markets()


# exchange.verbose = True  # uncomment for debugging purposes if necessary


# creating and canceling a linear swap (limit) order
symbol = 'ADA/USDT:USDT'
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
    # print(balance)

    # placing an order
    order = exchange.create_order(symbol, order_type, side, amount, price, params)
    # print(order)

    # listing open orders
    open_orders = exchange.fetch_open_orders(symbol)
    # print(open_orders)

    # canceling an order
    cancelOrder = exchange.cancel_order(order['id'], symbol)
    print(cancelOrder)
except Exception as e:
    print(type(e).__name__, str(e))


# creating and canceling inverse swap (limit) order
symbol = 'ADA/USD:ADA'
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
    # print(balance)

    # placing an order
    order = exchange.create_order(symbol, order_type, side, amount, price, params)
    print(order)

    # listing open orders
    open_orders = exchange.fetch_open_orders(symbol)
    # print(open_orders)

    # canceling an order
    cancelOrder = exchange.cancel_order(order['id'], symbol)
except Exception as e:
    print(type(e).__name__, str(e))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/huobi-swaps.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 92
- Code lines: 49
- Comment lines: 17
- Blank lines: 26

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

