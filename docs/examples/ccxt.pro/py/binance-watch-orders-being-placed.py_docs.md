# Documentation: examples/ccxt.pro/py/binance-watch-orders-being-placed.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-watch-orders-being-placed.py`
- **Size**: 1,752 bytes
- **Lines**: 60
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# Python
import ccxt.pro
from asyncio import run, gather
from pprint import pprint


async def place_delayed_order(exchange, symbol, amount, price):
    try:
        await exchange.sleep(5000)  # wait a bit
        order = await exchange.create_limit_buy_order(symbol, amount, price)
        print(exchange.iso8601(exchange.milliseconds()), 'place_delayed_order')
        pprint(order)
        print('---------------------------------------------------------------')
    except Exception as e:
        # break
        print(e)


async def watch_orders_loop(exchange, symbol):
    while True:
        try:
            orders = await exchange.watch_orders(symbol)
            print(exchange.iso8601(exchange.milliseconds()), 'watch_orders_loop', len(orders), ' last orders cached')
            print('---------------------------------------------------------------')
        except Exception as e:
            # break
            print(e)


async def watch_balance_loop(exchange):
    while True:
        try:
            balance = await exchange.watch_balance()
            print(exchange.iso8601(exchange.milliseconds()), 'watch_balance_loop')
            pprint(balance)
            print('---------------------------------------------------------------')
        except Exception as e:
            # break
            print(e)


async def main():
    exchange = ccxt.pro.binanceusdm({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })
    symbol = 'BTC/USDT'
    amount = 0.001
    price = 11111
    loops = [
        watch_orders_loop(exchange, symbol),
        watch_balance_loop(exchange),
        place_delayed_order(exchange, symbol, amount, price)
    ]
    await gather(*loops)
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-watch-orders-being-placed.py`.

**Functions defined**: watch_orders_loop, place_delayed_order, watch_balance_loop, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 45
- Comment lines: 4
- Blank lines: 11

### Main Components

**Functions** (4):
- `main()`
- `place_delayed_order()`
- `watch_balance_loop()`
- `watch_orders_loop()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations
- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/ccxt.pro/py/binance-watch-orders-being-placed.py
```

