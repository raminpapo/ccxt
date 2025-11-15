# Documentation: examples/ccxt.pro/py/many-exchanges-many-different-streams.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/many-exchanges-many-different-streams.py`
- **Size**: 1,946 bytes
- **Lines**: 57
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import ccxt.pro
from asyncio import gather, run


async def symbol_loop(exchange, method, symbol):
    print('Starting', exchange.id, method, symbol)
    while True:
        try:
            response = await getattr(exchange, method)(symbol)
            now = exchange.milliseconds()
            iso8601 = exchange.iso8601(now)
            if method == 'watchOrderBook':
                print(iso8601, exchange.id, method, symbol, response['asks'][0], response['bids'][0])
            elif method == 'watchTicker':
                print(iso8601, exchange.id, method, symbol, response['high'], response['low'], response['bid'], response['ask'])
            elif method == 'watchTrades':
                print(iso8601, exchange.id, method, symbol, len(response), 'trades')

        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails


async def method_loop(exchange, method, symbols):
    print('Starting', exchange.id, method, symbols)
    loops = [symbol_loop(exchange, method, symbol) for symbol in symbols]
    await gather(*loops)


async def exchange_loop(exchange_id, methods):
    print('Starting', exchange_id, methods)
    exchange = getattr(ccxt.pro, exchange_id)()
    loops = [method_loop(exchange, method, symbols) for method, symbols in methods.items()]
    await gather(*loops)
    await exchange.close()


async def main():
    exchanges = {
        'okex': {
            'watchOrderBook': ['BTC/USDT', 'ETH/BTC', 'ETH/USDT'],
            'watchTicker': ['BTC/USDT'],
        },
        'binance': {
            'watchOrderBook': ['BTC/USDT', 'ETH/BTC'],
            'watchTrades': [ 'ETH/BTC' ],
        },
    }
    loops = [exchange_loop(exchange_id, methods) for exchange_id, methods in exchanges.items()]
    await gather(*loops)


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/many-exchanges-many-different-streams.py`.

**Functions defined**: exchange_loop, main, symbol_loop, method_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 42
- Comment lines: 2
- Blank lines: 13

### Main Components

**Functions** (4):
- `exchange_loop()`
- `main()`
- `method_loop()`
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
python examples/ccxt.pro/py/many-exchanges-many-different-streams.py
```

