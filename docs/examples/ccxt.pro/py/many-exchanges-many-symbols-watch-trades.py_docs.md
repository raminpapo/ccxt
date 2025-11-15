# Documentation: examples/ccxt.pro/py/many-exchanges-many-symbols-watch-trades.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/many-exchanges-many-symbols-watch-trades.py`
- **Size**: 1,300 bytes
- **Lines**: 40
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import ccxt.pro
from asyncio import gather, run


async def symbol_loop(exchange, symbol):
    print('Starting the', exchange.id, 'symbol loop with', symbol)
    while True:
        try:
            trades = await exchange.watch_trades(symbol)
            now = exchange.milliseconds()
            print(exchange.iso8601(now), exchange.id, symbol, len(trades), trades[-1]['price'])
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails


async def exchange_loop(exchange_id, symbols):
    print('Starting the', exchange_id, 'exchange loop with', symbols)
    exchange = getattr(ccxt.pro, exchange_id)({
        'newUpdates': True,  # https://github.com/ccxt/ccxt/wiki/ccxt.pro.manual#incremental-data-structures
    })
    loops = [symbol_loop(exchange, symbol) for symbol in symbols]
    await gather(*loops)
    await exchange.close()


async def main():
    exchanges = {
        'okex': ['BTC/USDT', 'ETH/BTC', 'ETH/USDT'],
        'binance': ['BTC/USDT', 'ETH/BTC'],
    }
    loops = [exchange_loop(exchange_id, symbols) for exchange_id, symbols in exchanges.items()]
    await gather(*loops)


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/many-exchanges-many-symbols-watch-trades.py`.

**Functions defined**: exchange_loop, main, symbol_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 28
- Comment lines: 2
- Blank lines: 10

### Main Components

**Functions** (3):
- `exchange_loop()`
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
python examples/ccxt.pro/py/many-exchanges-many-symbols-watch-trades.py
```

