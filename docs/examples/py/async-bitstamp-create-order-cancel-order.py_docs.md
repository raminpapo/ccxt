# Documentation: examples/py/async-bitstamp-create-order-cancel-order.py

## File Metadata

- **Path**: `examples/py/async-bitstamp-create-order-cancel-order.py`
- **Size**: 1,801 bytes
- **Lines**: 57
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run
import ccxt.async_support as ccxt
from pprint import pprint


print('CCXT Version:', ccxt.__version__)


async def main():
    exchange = ccxt.bitstamp({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'uid': 'YOUR_UID',
    })
    markets = await exchange.load_markets()
    exchange.verbose = True  # enable verbose mode after loading the markets
    print('-------------------------------------------------------------------')
    try:
        balance = await exchange.fetch_balance()
        pprint(balance)
    except Exception as e:
        print('Failed to fetch the balance')
        print(type(e).__name__, str(e))
    order = None
    print('-------------------------------------------------------------------')
    try:
        symbol = 'BTC/USDT'
        market = exchange.market(symbol)
        base = market['base']
        quote = market['quote']
        pprint(balance[base])
        pprint(balance[quote])
        amount = 0.001
        price = 40000
        order_type = 'limit'
        side = 'sell'
        order = await exchange.create_order(symbol, order_type, side, amount, price)
        pprint(order)
    except Exception as e:
        print('Failed to place', symbol, 'order')
        print(type(e).__name__, str(e))
    print('-------------------------------------------------------------------')
    if order is not None:
        try:
            response = await exchange.cancel_order(order['id'], order['symbol'])
            pprint(response)
        except Exception as e:
            print('Failed to cancel', symbol, 'order')
            print(type(e).__name__, str(e))
    print('-------------------------------------------------------------------')
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-bitstamp-create-order-cancel-order.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 48
- Comment lines: 1
- Blank lines: 8

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
python examples/py/async-bitstamp-create-order-cancel-order.py
```

