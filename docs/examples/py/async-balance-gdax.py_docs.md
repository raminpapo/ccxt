# Documentation: examples/py/async-balance-gdax.py

## File Metadata

- **Path**: `examples/py/async-balance-gdax.py`
- **Size**: 609 bytes
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
    gdax = ccxt.gdax({
        'apiKey': "YOUR_API_KEY",
        'secret': "YOUR_SECRET",
        'password': "YOUR_PASSWORD",
        'verbose': True,  # switch it to False if you don't want the HTTP log
    })
    # move gdax to sandbox
    gdax.urls['api'] = 'https://api-public.sandbox.gdax.com'
    print(await gdax.fetch_balance())


asyncio.run(test())

```

## High-Level Overview

This is a Python file located at `examples/py/async-balance-gdax.py`.

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

- `https://api-public.sandbox.gdax.com` (referenced)



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-balance-gdax.py
```

