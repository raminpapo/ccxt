# Documentation: examples/ccxt.pro/py/kucoin-watch-multiple-orderbooks.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/kucoin-watch-multiple-orderbooks.py`
- **Size**: 993 bytes
- **Lines**: 32
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
            orderbook = await exchange.watch_order_book(symbol)
            now = exchange.milliseconds()
            print(exchange.iso8601(now), exchange.id, symbol, orderbook['asks'][0], orderbook['bids'][0])
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails

async def main():
    exchange = ccxt.pro.kucoin({
        "apiKey": "YOUR_API_KEY",
        "secret": "YOUR_API_SECRET",
        "password": "YOUR_API_PASSWORD",
    })
    symbols = ['KDA/USDT', 'KDA/BTC', 'BTC/USDT']
    loops = [symbol_loop(exchange, symbol) for symbol in symbols]
    await gather(*loops)
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/kucoin-watch-multiple-orderbooks.py`.

**Functions defined**: main, symbol_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 23
- Comment lines: 2
- Blank lines: 7

### Main Components

**Functions** (2):
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
python examples/ccxt.pro/py/kucoin-watch-multiple-orderbooks.py
```

