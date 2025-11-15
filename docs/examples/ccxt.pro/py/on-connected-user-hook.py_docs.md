# Documentation: examples/ccxt.pro/py/on-connected-user-hook.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/on-connected-user-hook.py`
- **Size**: 1,554 bytes
- **Lines**: 56
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run, ensure_future
from pprint import pprint


print('CCXT Version:', ccxt.__version__)


# on_connected() is called when a client connection is established
# note that the exchange will reuse the same client connection
# some exchanges might require two or more public/private connections
# therefore on_connected() may be called more than once

class MyBinance(ccxt.pro.binance):
    def on_connected(self, client, message=None):
        print('Connected to', client.url)
        ensure_future(create_order(self))


async def create_order(exchange):
    symbol = 'BTC/USDT'
    type = 'limit'
    side = 'buy'
    amount = 123.45  # change for your values
    price = 54.321  # change for your values
    params = {}
    try:
        order = await exchange.create_order(symbol, type, side, amount, price, params)
        print('--------------------------------------------------------------')
        print('create_order():')
        pprint(order)
    except Exception as e:
        print(type(e).__name__, str(e))


async def watch_orders(exchange):
    while True:
        try:
            orders = await exchange.watch_orders()
            print('--------------------------------------------------------------')
            print('watch_orders():')
            pprint(orders)
        except Exception as e:
            print(type(e).__name__, str(e))
            break
    await exchange.close()


exchange = MyBinance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})


run(watch_orders(exchange))

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/on-connected-user-hook.py`.

**Classes defined**: MyBinance

**Functions defined**: watch_orders, on_connected, create_order

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 38
- Comment lines: 4
- Blank lines: 14

### Main Components

**Classes** (1):
- `MyBinance`

**Functions** (3):
- `create_order()`
- `on_connected()`
- `watch_orders()`



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
python examples/ccxt.pro/py/on-connected-user-hook.py
```

