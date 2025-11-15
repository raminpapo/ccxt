# Documentation: examples/ccxt.pro/py/watch-many-exchanges-many-tickers.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/watch-many-exchanges-many-tickers.py`
- **Size**: 1,261 bytes
- **Lines**: 40
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run, gather
import ccxt.pro


print('CCXT Version:', ccxt.__version__)


async def exchange_loop(exchange_id, symbols):
    exchange = getattr(ccxt.pro, exchange_id)()
    markets = await exchange.load_markets()
    await gather(*[watch_ticker_loop(exchange, symbol) for symbol in symbols])
    await exchange.close()


async def watch_ticker_loop(exchange, symbol):
    # exchange.verbose = True  # uncomment for debugging purposes if necessary
    while True:
        try:
            ticker = await exchange.watch_ticker(symbol)
            now = exchange.milliseconds()
            print(exchange.iso8601(now), exchange.id, symbol, 'bid:', ticker['bid'], 'ask:', ticker['ask'], 'last:', ticker['last'], 'on', ticker['datetime'])
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails


async def main():
    exchanges = {
        'binance': [ 'BTC/USDT', 'ETH/USDT' ],
        'ftx': [ 'BTC/USD', 'ETH/USD' ],
    }
    loops = [exchange_loop(exchange_id, symbols) for exchange_id, symbols in exchanges.items()]
    await gather(*loops)


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/watch-many-exchanges-many-tickers.py`.

**Functions defined**: exchange_loop, main, watch_ticker_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 25
- Comment lines: 3
- Blank lines: 12

### Main Components

**Functions** (3):
- `exchange_loop()`
- `main()`
- `watch_ticker_loop()`



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
python examples/ccxt.pro/py/watch-many-exchanges-many-tickers.py
```

