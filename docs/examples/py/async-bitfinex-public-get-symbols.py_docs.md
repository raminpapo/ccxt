# Documentation: examples/py/async-bitfinex-public-get-symbols.py

## File Metadata

- **Path**: `examples/py/async-bitfinex-public-get-symbols.py`
- **Size**: 528 bytes
- **Lines**: 24
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
    bitfinex = ccxt.bitfinex({
        'apiKey': "YOUR_API_KEY",
        'secret': "YOUR_SECRET",
        'verbose': True,  # switch it to False if you don't want the HTTP log
    })
    print(await bitfinex.public_get_symbols())
    await bitfinex.close()


asyncio.run(test())

```

## High-Level Overview

This is a Python file located at `examples/py/async-bitfinex-public-get-symbols.py`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 15
- Comment lines: 1
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
python examples/py/async-bitfinex-public-get-symbols.py
```

