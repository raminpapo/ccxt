# Documentation: examples/py/async-bybit-transfer.py

## File Metadata

- **Path**: `examples/py/async-bybit-transfer.py`
- **Size**: 1,078 bytes
- **Lines**: 33
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
    exchange = ccxt.bybit({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # 'verbose': True,  # for debug output
    })
    await exchange.load_markets()
    try:
        pprint(await exchange.fetch_transfers())  # Fetch your transfer history
        # pprint(await exchange.transfer('USDT', 1.0, 'swap', 'spot'))  # Transfer to the spot wallet
        # pprint(await exchange.transfer('USDT', 1.0, 'spot', 'future'))  # Transfer to the Derivatives wallet
        # pprint(await exchange.transfer('USDT', 1.0, 'spot', 'swap'))  # Transfer to the Derivatives wallet
        # pprint(await exchange.transfer('USDC', 1.0, 'spot', 'option'))  # Transfer to the USDC Derivatives wallet
    except Exception as e:
        print(e)
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-bybit-transfer.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 19
- Comment lines: 6
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
python examples/py/async-bybit-transfer.py
```

