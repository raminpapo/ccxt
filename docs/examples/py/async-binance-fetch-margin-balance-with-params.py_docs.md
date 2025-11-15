# Documentation: examples/py/async-binance-fetch-margin-balance-with-params.py

## File Metadata

- **Path**: `examples/py/async-binance-fetch-margin-balance-with-params.py`
- **Size**: 670 bytes
- **Lines**: 31
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })
    while True:
        try:
            balance = await exchange.fetch_balance({'type': 'margin'})
            pprint(balance)
        except Exception as e:
            print('fetch_balance() failed')
            print(e)
            break
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-binance-fetch-margin-balance-with-params.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 22
- Comment lines: 1
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
python examples/py/async-binance-fetch-margin-balance-with-params.py
```

