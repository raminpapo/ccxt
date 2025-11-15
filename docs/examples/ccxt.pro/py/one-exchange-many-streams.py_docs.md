# Documentation: examples/ccxt.pro/py/one-exchange-many-streams.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/one-exchange-many-streams.py`
- **Size**: 797 bytes
- **Lines**: 26
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run
import ccxt.pro

async def loop(exchange, symbol):
    await exchange.throttle(10)
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            now = exchange.milliseconds()
            print(exchange.iso8601(now), symbol, orderbook['asks'][0], orderbook['bids'][0])
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            # break  # you can also break just this one loop if it fails

async def main():
    exchange = ccxt.pro.ftx()
    symbols = ['BTC/USDT', 'ETH/USDT', 'ETH/BTC']
    await asyncio.gather(*[loop(exchange, symbol) for symbol in symbols])
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/one-exchange-many-streams.py`.

**Functions defined**: loop, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 17
- Comment lines: 3
- Blank lines: 6

### Main Components

**Functions** (2):
- `loop()`
- `main()`



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
python examples/ccxt.pro/py/one-exchange-many-streams.py
```

