# Documentation: examples/ccxt.pro/py/many-exchanges.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/many-exchanges.py`
- **Size**: 880 bytes
- **Lines**: 31
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import ccxt.pro


async def loop(exchange_id, symbol):
    exchange = getattr(ccxt.pro, exchange_id)()
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            now = exchange.milliseconds()
            print(exchange.iso8601(now), exchange.id, symbol, orderbook['asks'][0], orderbook['bids'][0])
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails
    await exchange.close()


async def main():
    symbols = {
        'kraken': 'BTC/USDT',
        'binance': 'BTC/USDT',
        'bitmex': 'XBT_USDT',
    }
    await asyncio.gather(*[loop(exchange_id, symbol) for exchange_id, symbol in symbols.items()])


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/many-exchanges.py`.

**Functions defined**: loop, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 21
- Comment lines: 2
- Blank lines: 8

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
python examples/ccxt.pro/py/many-exchanges.py
```

