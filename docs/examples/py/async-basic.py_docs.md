# Documentation: examples/py/async-basic.py

## File Metadata

- **Path**: `examples/py/async-basic.py`
- **Size**: 445 bytes
- **Lines**: 22
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


async def test_binance():
    exchange = ccxt.binance()
    markets = await exchange.load_markets()
    await exchange.close()
    return markets


if __name__ == '__main__':
    print(asyncio.run(test_binance()))

```

## High-Level Overview

This is a Python file located at `examples/py/async-basic.py`.

**Functions defined**: test_binance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 13
- Comment lines: 1
- Blank lines: 8

### Main Components

**Functions** (1):
- `test_binance()`



## Usage Examples

### Main execution block:

```python
print(asyncio.run(test_binance()))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-basic.py
```

