# Documentation: examples/py/async-basic-orderbook.py

## File Metadata

- **Path**: `examples/py/async-basic-orderbook.py`
- **Size**: 685 bytes
- **Lines**: 30
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


async def test():

    exchange = ccxt.okex({
        # 'proxy': 'https://cors-anywhere.herokuapp.com/',
        # 'origin': 'foobar',  # when using CORS proxies, set this to some random string
    })

    try:
        orderbook = await exchange.fetch_order_book('BTC/USDT')
        await exchange.close()
        return orderbook
    except ccxt.BaseError as e:
        print(type(e).__name__, str(e), str(e.args))
        raise e


asyncio.run(test())

```

## High-Level Overview

This is a Python file located at `examples/py/async-basic-orderbook.py`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 17
- Comment lines: 3
- Blank lines: 10

### Main Components

**Functions** (1):
- `test()`



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
python examples/py/async-basic-orderbook.py
```

