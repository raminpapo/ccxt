# Documentation: examples/ccxt.pro/py/spot-vs-future-arbitrage-bitmart.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/spot-vs-future-arbitrage-bitmart.py`
- **Size**: 2,330 bytes
- **Lines**: 67
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-
 
import asyncio
import sys
import os

# ------------------------------------------------------------------------------

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__)))))
sys.path.append(root + '/python')

# ------------------------------------------------------------------------------

import ccxt.pro

print('CCXT Version:', ccxt.pro.__version__)

orderbooks = {}

def handle_all_orderbooks(exchange, orderbooks, spot, future):
    if spot in orderbooks and future in orderbooks: 
        spot_order_book = orderbooks[spot]
        future_order_book = orderbooks[future]
        timestamp = exchange.milliseconds()
        spot_lag = abs(timestamp - spot_order_book['timestamp']) if spot_order_book['timestamp'] else 10000
        future_lag = abs(timestamp - future_order_book['timestamp']) if future_order_book['timestamp'] else 10000
        if spot_lag >= 10000 or future_lag >= 10000:
            print('Lag > 10 seconds')

async def symbol_loop(exchange, symbol, spot, future):
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            orderbooks[symbol] = orderbook
            print(exchange.id, '{:13s}'.format(symbol), orderbook['datetime'], orderbook['asks'][0], orderbook['bids'][0])
            #
            # here you can do what you want
            # with the most recent versions of each orderbook you have so far
            #
            # you can also wait until all of them are available
            # by just looking into all the orderbooks and counting them
            #
            # we just print them here to keep this example simple
            #
            handle_all_orderbooks(exchange, orderbooks, spot, future)
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails


async def main():
    spot = 'BTC/USDT'
    future = 'BTC/USDT:USDT'
    symbols = [ spot, future ]
    exchange = ccxt.pro.bitmart()
    loops = [
        symbol_loop(exchange, spot, spot, future),
        symbol_loop(exchange, future, spot, future),
    ]
    await asyncio.gather(*loops)
    await exchange.close()


asyncio.run(main())


```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/spot-vs-future-arbitrage-bitmart.py`.

**Functions defined**: handle_all_orderbooks, main, symbol_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 39
- Comment lines: 13
- Blank lines: 15

### Main Components

**Functions** (3):
- `handle_all_orderbooks()`
- `main()`
- `symbol_loop()`



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
python examples/ccxt.pro/py/spot-vs-future-arbitrage-bitmart.py
```

