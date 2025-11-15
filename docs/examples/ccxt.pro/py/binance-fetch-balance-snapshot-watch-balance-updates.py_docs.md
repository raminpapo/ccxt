# Documentation: examples/ccxt.pro/py/binance-fetch-balance-snapshot-watch-balance-updates.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-fetch-balance-snapshot-watch-balance-updates.py`
- **Size**: 1,634 bytes
- **Lines**: 54
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import ccxt.pro
from asyncio import run


print('CCXT Version:', ccxt.__version__)


# This example will run silent and will return your balance only when the balance is updated.
#
# 1. launch the example with your keys and keep it running
# 2. go to the trading section on the website
# 3. place a order on a spot market
# 4. see your balance updated in the example
#
# Warning! This example might produce a lot of output to your screen


async def watch_balance(exchange):
    await exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes if necessary
    balance = await exchange.fetch_balance()
    print('---------------------------------------------------------')
    print(exchange.iso8601(exchange.milliseconds()))
    print(balance)
    print('')
    while True:
        try:
            update = await exchange.watch_balance()
            balance = exchange.deep_extend(balance, update)
            # it will print the balance update when the balance changes
            # if the balance remains unchanged the exchange will not send it
            print('---------------------------------------------------------')
            print(exchange.iso8601(exchange.milliseconds()))
            print(balance)
            print('')
        except Exception as e:
            print('watch_balance() failed')
            print(type(e).__name__, str(e))
            break


async def main():
    exchange = ccxt.pro.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })
    await watch_balance(exchange)
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-fetch-balance-snapshot-watch-balance-updates.py`.

**Functions defined**: watch_balance, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 30
- Comment lines: 12
- Blank lines: 12

### Main Components

**Functions** (2):
- `main()`
- `watch_balance()`



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
python examples/ccxt.pro/py/binance-fetch-balance-snapshot-watch-balance-updates.py
```

