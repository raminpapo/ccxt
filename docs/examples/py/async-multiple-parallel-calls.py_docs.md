# Documentation: examples/py/async-multiple-parallel-calls.py

## File Metadata

- **Path**: `examples/py/async-multiple-parallel-calls.py`
- **Size**: 1,681 bytes
- **Lines**: 53
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')


import ccxt.async_support as ccxt
from asyncio import run, gather

print('CCXT Version:', ccxt.__version__)

# This example demonstrates how to execute multiple requests asynchronously.
# The requests will be executed in parallel independently of each other.
# In order to let them run in parallel the user has to disable the rate limiter.
# Disabling the rate limiter is not recommended, unless you really know
# what you are doing! If you are too aggressive with your requests and
# you don't do proper request timing precisely, the exchange can ban you!
# https://github.com/ccxt/ccxt/wiki/
# https://github.com/ccxt/ccxt/wiki/Manual
# https://github.com/ccxt/ccxt/wiki/Manual#rate-limit


async def main():
    exchange = ccxt.ftx({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'enableRateLimit': False,  # not recommended
    })
    markets = await exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes
    symbol = 'BTC/USDT'
    loops = [
        exchange.fetch_balance(),
        exchange.fetch_order_book(symbol),
        exchange.fetch_open_orders()
    ]
    results = await gather(*loops)
    print('Balance:')
    print(results[0])
    print('------------------------------------------------------------------')
    print(symbol, 'orderbook:')
    print(results[1])
    print('------------------------------------------------------------------')
    print('Open orders:')
    print(results[2])
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-multiple-parallel-calls.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 31
- Comment lines: 11
- Blank lines: 11

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
python examples/py/async-multiple-parallel-calls.py
```

