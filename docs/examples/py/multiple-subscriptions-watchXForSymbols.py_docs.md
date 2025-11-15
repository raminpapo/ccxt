# Documentation: examples/py/multiple-subscriptions-watchXForSymbols.py

## File Metadata

- **Path**: `examples/py/multiple-subscriptions-watchXForSymbols.py`
- **Size**: 1,414 bytes
- **Lines**: 59
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
from random import randint
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.pro as ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.binance({})


async def watch_multiple_trades(symbols):
    while True:
        trades = await exchange.watch_trades_for_symbols(symbols)
        print(f'trade: {trades[0]["symbol"], trades[0]["price"]}')


async def watch_multiple_orderbooks(symbols):
    while True:
        orderbooks = await exchange.watch_order_book_for_symbols(symbols)
        print(f'orderbook bid: {orderbooks["symbol"]}{orderbooks["bids"][0]}')



async def watch_multiple_ohlcv(symbols):
    while True:
        ohlcv = await exchange.watch_ohlcv_for_symbols(symbols)
        print(f'ohlcv: {ohlcv}')



async def example_1():

    await asyncio.gather(
        watch_multiple_trades(['BTC/USDT', 'ADA/USDT', 'ETH/USDT']),
        watch_multiple_orderbooks(['BTC/USDT', 'ETH/USDT']),
        watch_multiple_ohlcv([['BTC/USDT', '1m'], ['LTC/USDT', '1m']]),
    )

# -------------------------------------------------------------------------------------------

async def main():
    try:
        await example_1()
    except Exception as e:
        print(e)
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/multiple-subscriptions-watchXForSymbols.py`.

**Functions defined**: watch_multiple_trades, main, example_1, watch_multiple_ohlcv, watch_multiple_orderbooks

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 35
- Comment lines: 2
- Blank lines: 22

### Main Components

**Functions** (5):
- `example_1()`
- `main()`
- `watch_multiple_ohlcv()`
- `watch_multiple_orderbooks()`
- `watch_multiple_trades()`



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
python examples/py/multiple-subscriptions-watchXForSymbols.py
```

