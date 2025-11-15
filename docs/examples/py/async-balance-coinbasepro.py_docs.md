# Documentation: examples/py/async-balance-coinbasepro.py

## File Metadata

- **Path**: `examples/py/async-balance-coinbasepro.py`
- **Size**: 607 bytes
- **Lines**: 26
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
    exchange = ccxt.coinbasepro({
        'apiKey': "YOUR_API_KEY",
        'secret': "YOUR_SECRET",
        'password': "YOUR_PASSWORD",
        'verbose': True,  # switch it to False if you don't want the HTTP log
    })
    # move to sandbox
    exchange.urls['api'] = exchange.urls['test']
    print(await exchange.fetch_balance())


asyncio.run(test())

```

## High-Level Overview

This is a Python file located at `examples/py/async-balance-coinbasepro.py`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 16
- Comment lines: 2
- Blank lines: 8

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
python examples/py/async-balance-coinbasepro.py
```

