# Documentation: examples/ccxt.pro/py/watch-all-symbols.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/watch-all-symbols.py`
- **Size**: 1,178 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import ccxt.pro


async def loop(exchange, symbol, n):
    i = 0
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            # print every 100th bidask to avoid wasting CPU cycles on printing
            if not i % 100:
                # i = how many updates there were in total
                # n = the number of the pair to count subscriptions
                now = exchange.milliseconds()
                print(exchange.iso8601(now), n, symbol, i, orderbook['asks'][0], orderbook['bids'][0])
            i += 1
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            # break  # you can also break just this one loop if it fails


async def main():
    exchange = ccxt.pro.kraken()
    await exchange.load_markets()
    markets = list(exchange.markets.values())
    symbols = [market['symbol'] for market in markets if not market['darkpool']]
    await asyncio.gather(*[loop(exchange, symbol, n) for n, symbol in enumerate(symbols)])
    await exchange.close()



asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/watch-all-symbols.py`.

**Functions defined**: loop, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 21
- Comment lines: 6
- Blank lines: 9

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
python examples/ccxt.pro/py/watch-all-symbols.py
```

