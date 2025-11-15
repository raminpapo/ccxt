# Documentation: examples/py/async-ticker.py

## File Metadata

- **Path**: `examples/py/async-ticker.py`
- **Size**: 527 bytes
- **Lines**: 25
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


async def test(id, symbol):
    exchange = getattr(ccxt, id)()
    ticker = await exchange.fetch_ticker(symbol)
    await exchange.close()
    return ticker


if __name__ == '__main__':
    id = 'binance'
    symbol = 'ETH/BTC'
    pprint(asyncio.run(test(id, symbol)))

```

## High-Level Overview

This is a Python file located at `examples/py/async-ticker.py`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 16
- Comment lines: 1
- Blank lines: 8

### Main Components

**Functions** (1):
- `test()`



## Usage Examples

### Main execution block:

```python
id = 'binance'
    symbol = 'ETH/BTC'
    pprint(asyncio.run(test(id, symbol)))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-ticker.py
```

