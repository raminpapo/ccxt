# Documentation: examples/py/async-instantiate-all-at-once.py

## File Metadata

- **Path**: `examples/py/async-instantiate-all-at-once.py`
- **Size**: 656 bytes
- **Lines**: 26
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import asyncio

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402

exchanges = {}  # a placeholder for your instances


async def main():
    for id in ccxt.exchanges:
        exchange = getattr(ccxt, id)
        exchanges[id] = exchange()
    # now exchanges dictionary contains all exchange instances...
    print(await exchanges['bittrex'].fetch_order_book('ETH/BTC'))
    # close the aiohttp session object
    for id in exchanges:
        await exchanges[id].close()

asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-instantiate-all-at-once.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 15
- Comment lines: 3
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
python examples/py/async-instantiate-all-at-once.py
```

