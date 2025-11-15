# Documentation: wiki/examples/py/gateio-swaps.md

## File Metadata

- **Path**: `wiki/examples/py/gateio-swaps.md`
- **Size**: 1,788 bytes
- **Lines**: 83
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Gateio Swaps](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
from random import randint
import sys


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.gateio({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'options': {
        'defaultType': 'future',
    },
})

markets = exchange.load_markets()

# exchange.verbose = True  # uncomment for debugging purposes if necessary

# Example 1: Creating and canceling a linear future (limit) order
symbol = 'LTC/USDT:USDT'
type = 'limit'
side = 'buy'
amount = 1
price = 55

try:
    # placing an order
    order = exchange.create_order(symbol, type, side, amount, price)
    print(order)

    # listing open orders
    open_orders = exchange.fetch_open_orders(symbol)
    print(open_orders)

    # canceling an order
    cancelOrder = exchange.cancel_order(order['id'], symbol)
    print(cancelOrder)
except Exception as e:
    print(type(e).__name__, str(e))


# Example 2: Creating and canceling a linear future (stop-limit) order with leverage
symbol = 'LTC/USDT:USDT'
type = 'limit'
side = 'buy'
amount = 1
price = 55
stop_price = 140
params = {'stopPrice': stop_price }

try:
    # set leverage
    leverage = exchange.set_leverage(3, symbol)
    print(leverage)

    # placing an order
    order = exchange.create_order(symbol, type, side, amount, price, params)
    print(order)

    # listing open orders
    open_orders = exchange.fetch_open_orders(symbol)
    print(open_orders)

    # canceling an order
    cancelParams = {'isStop': True }
    cancelOrder = exchange.cancel_order(order['id'], symbol, cancelParams)
    print(cancelOrder)

    # reset leverage
    exchange.set_leverage(1, symbol)
except Exception as e:
    print(type(e).__name__, str(e)) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/gateio-swaps.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 83
- Code lines: 50
- Comment lines: 12
- Blank lines: 21

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

