# Documentation: examples/py/async-gdax-fetch-order-book-continuously.py

## File Metadata

- **Path**: `examples/py/async-gdax-fetch-order-book-continuously.py`
- **Size**: 743 bytes
- **Lines**: 25
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def main(symbol):
    exchange = ccxt.binance()
    while True:
        print('--------------------------------------------------------------')
        print(exchange.iso8601(exchange.milliseconds()), 'fetching', symbol, 'ticker from', exchange.name)
        # this can be any call really
        ticker = await exchange.fetch_order_book(symbol)
        print(exchange.iso8601(exchange.milliseconds()), 'fetched', symbol, 'ticker from', exchange.name)
        print(ticker)


asyncio.run(main('BTC/USDT'))

```

## High-Level Overview

This is a Python file located at `examples/py/async-gdax-fetch-order-book-continuously.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 15
- Comment lines: 2
- Blank lines: 8

### Main Components

**Functions** (1):
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
python examples/py/async-gdax-fetch-order-book-continuously.py
```

