# Documentation: examples/py/async-bittrex-orderbook.py

## File Metadata

- **Path**: `examples/py/async-bittrex-orderbook.py`
- **Size**: 634 bytes
- **Lines**: 30
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys

if not sys.version >= '3.6':
    print('This script requires Python 3.6+')
    sys.exit()

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def poll():
    exchange = ccxt.bittrex()
    while True:
        yield await exchange.fetch_order_book('BTC/USDT')
        await asyncio.sleep(exchange.rateLimit / 1000)


async def main():
    async for orderbook in poll():
        print(orderbook['bids'][0], orderbook['asks'][0])


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-bittrex-orderbook.py`.

**Functions defined**: main, poll

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 18
- Comment lines: 1
- Blank lines: 11

### Main Components

**Functions** (2):
- `main()`
- `poll()`



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
python examples/py/async-bittrex-orderbook.py
```

