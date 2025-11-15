# Documentation: examples/ccxt.pro/py/many-exchanges-many-orderbooks-synchronized.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/many-exchanges-many-orderbooks-synchronized.py`
- **Size**: 1,993 bytes
- **Lines**: 60
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import ccxt.pro


orderbooks = {}


def handle_all_orderbooks(orderbooks):
    print('We have the following orderbooks:')
    for exchange_id, orderbooks_by_symbol in orderbooks.items():
        for symbol in orderbooks_by_symbol.keys():
            orderbook = orderbooks_by_symbol[symbol]
            print(ccxt.pro.Exchange.iso8601(orderbook['timestamp']), exchange_id, symbol, orderbook['asks'][0], orderbook['bids'][0])


async def symbol_loop(exchange, symbol):
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            orderbooks[exchange.id] = orderbooks.get(exchange.id, {})
            orderbooks[exchange.id][symbol] = orderbook
            print('===========================================================')
            #
            # here you can do what you want
            # with the most recent versions of each orderbook you have so far
            #
            # you can also wait until all of them are available
            # by just looking into all the orderbooks and counting them
            #
            # we just print them here to keep this example simple
            #
            handle_all_orderbooks(orderbooks)
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails


async def exchange_loop(exchange_id, symbols):
    exchange = getattr(ccxt.pro, exchange_id)()
    loops = [symbol_loop(exchange, symbol) for symbol in symbols]
    await asyncio.gather(*loops)
    await exchange.close()


async def main():
    symbols = ['BTC/USDT', 'ETH/BTC']
    # symbols = []
    exchanges = {
        'okex': symbols + ['ETH/USDT'],
        'binance': symbols,
    }
    loops = [exchange_loop(exchange_id, symbols) for exchange_id, symbols in exchanges.items()]
    await asyncio.gather(*loops)


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/many-exchanges-many-orderbooks-synchronized.py`.

**Functions defined**: handle_all_orderbooks, exchange_loop, main, symbol_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 34
- Comment lines: 12
- Blank lines: 14

### Main Components

**Functions** (4):
- `exchange_loop()`
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
python examples/ccxt.pro/py/many-exchanges-many-orderbooks-synchronized.py
```

