# Documentation: examples/ccxt.pro/py/binance-spot-and-futures.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-spot-and-futures.py`
- **Size**: 2,335 bytes
- **Lines**: 74
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import ccxt.pro
from asyncio import gather, run


orderbooks = {}


def handle_all_orderbooks(orderbooks):
    print('We have the following orderbooks:')
    for id, orderbooks_by_symbol in orderbooks.items():
        for symbol in orderbooks_by_symbol.keys():
            orderbook = orderbooks_by_symbol[symbol]
            print(ccxt.pro.Exchange.iso8601(orderbook['timestamp']), id, symbol, orderbook['asks'][0], orderbook['bids'][0])


async def symbol_loop(exchange, id, symbol):
    print('Starting', id, symbol)
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            orderbooks[id] = orderbooks.get(id, {})
            orderbooks[id][symbol] = orderbook
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


async def exchange_loop(id, config):
    print('Starting', id)
    exchange = getattr(ccxt.pro, config['id'])({
        'options': config['options'],
    })
    loops = [symbol_loop(exchange, id, symbol) for symbol in config['symbols']]
    await gather(*loops)
    await exchange.close()


async def main():
    configs = {
        'Exchange A (Binance spot)': {
            'id': 'binance',
            'symbols': ['BTC/USDT', 'ETH/BTC','ETH/USDT'],
            'options': {
                'defaultType': 'spot',
            },
        },
        'Exchange B (Binance futures)': {
            'id': 'binance',
            'symbols': ['BTC/USDT', 'ETH/USDT'],
            'options': {
                'defaultType': 'future',
            },
        },
    }
    loops = [exchange_loop(id, config) for id, config in configs.items()]
    await gather(*loops)


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-spot-and-futures.py`.

**Functions defined**: handle_all_orderbooks, exchange_loop, main, symbol_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 74
- Code lines: 49
- Comment lines: 11
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
python examples/ccxt.pro/py/binance-spot-and-futures.py
```

