# Documentation: examples/py/async-fetch-balance.py

## File Metadata

- **Path**: `examples/py/async-fetch-balance.py`
- **Size**: 930 bytes
- **Lines**: 31
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
    exchange = ccxt.bitstamp({
        # "verbose": True,  # useful for debugging purposes, uncomment if needed
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'uid': 'YOUR_UID',
        # i'm adding a CORS proxy here, because my country is blocked by bitstamp
        # you don't need this, so it's safe to comment it out
        # "proxy": "https://cors-anywhere.herokuapp.com/",
        # "origin": "bitstamp"
    })
    print(await exchange.fetch_balance())
    await exchange.close()  # don't forget to close it when you're done
    return True

if __name__ == '__main__':
    print('CCXT version:', ccxt.__version__)
    print(asyncio.run(test()))

```

## High-Level Overview

This is a Python file located at `examples/py/async-fetch-balance.py`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 18
- Comment lines: 6
- Blank lines: 7

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

### Main execution block:

```python
print('CCXT version:', ccxt.__version__)
    print(asyncio.run(test()))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-fetch-balance.py
```

