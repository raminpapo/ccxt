# Documentation: examples/py/async-okx-margin-borrow.py

## File Metadata

- **Path**: `examples/py/async-okx-margin-borrow.py`
- **Size**: 974 bytes
- **Lines**: 38
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
    exchange = ccxt.okx({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # okx requires this: https://github.com/ccxt/ccxt/wiki/Manual#authentication
        'password': 'YOUR_API_PASSWORD',
        # 'verbose': True,  # for debug output
    })
    await exchange.load_markets()
    code = 'BTC'
    amount = 1
    try:
        response = await exchange.borrowCrossMargin(code, amount)
        pprint(response)
    except ccxt.InsufficientFunds as e:
        print('borrowCrossMargin() failed – not enough funds')
        print(e)
    except Exception as e:
        print('borrowCrossMargin() failed')
        print(e)
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-okx-margin-borrow.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 27
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
python examples/py/async-okx-margin-borrow.py
```

