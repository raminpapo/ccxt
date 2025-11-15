# Documentation: examples/py/async-generator-basic.py

## File Metadata

- **Path**: `examples/py/async-generator-basic.py`
- **Size**: 445 bytes
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


async def poll():
    exchange = ccxt.poloniex()
    while True:
        yield await exchange.fetch_ticker('ETH/BTC')


async def main():
    async for ticker in poll():
        print(ticker)


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-generator-basic.py`.

**Functions defined**: main, poll

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 14
- Comment lines: 1
- Blank lines: 10

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
python examples/py/async-generator-basic.py
```

