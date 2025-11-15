# Documentation: examples/py/async-okx-positional-orders.py

## File Metadata

- **Path**: `examples/py/async-okx-positional-orders.py`
- **Size**: 2,158 bytes
- **Lines**: 61
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
from pprint import pprint
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402
# or
# import ccxtpro as ccxt


print('CCXT Version:', ccxt.__version__)


async def main():
    exchange = ccxt.okx({
        'apiKey': 'YOUR_API_KEY',  # https://github.com/ccxt/ccxt/wiki/Manual#authentication
        'secret': 'YOUR_API_SECRET',
        'password': 'YOUR_API_PASSWORD',
        'options': {
            'defaultType': 'future',
        },
    })
    try:
        markets = await exchange.load_markets()
        exchange.verbose = True  # uncomment for debugging
        print('---------------------------------------------------------------')
        print('Futures balance:')
        futures_balance = await exchange.fetch_balance()
        pprint(futures_balance)
        print('---------------------------------------------------------------')
        print('Futures symbols:')
        print([market['symbol'] for market in markets.values() if market['future']])
        print('---------------------------------------------------------------')
        symbol = 'BTC/USDT:USDT-201225'  # a futures symbol
        market = exchange.market(symbol)
        pprint(market)
        print('---------------------------------------------------------------')
        type = '1'  # 1:open long 2:open short 3:close long 4:close short for futures
        side = None  # irrelevant for futures
        amount = 1  # how many contracts you want to buy or sell
        price = 17000  # limit price
        params = {
            # 'order_type': '4',  # uncomment for a market order, makes limit price irrelevant
            # 'leverage': '10',  # or '20'
        }
        order = await exchange.create_order(symbol, type, side, amount, price, params)
        print('Order:')
        pprint(order)
        print('---------------------------------------------------------------')
    except Exception as e:
        print(type(e).__name__, str(e))
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-okx-positional-orders.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 46
- Comment lines: 5
- Blank lines: 10

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-okx-positional-orders.py
```

