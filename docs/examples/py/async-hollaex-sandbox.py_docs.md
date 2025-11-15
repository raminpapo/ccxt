# Documentation: examples/py/async-hollaex-sandbox.py

## File Metadata

- **Path**: `examples/py/async-hollaex-sandbox.py`
- **Size**: 669 bytes
- **Lines**: 34
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from asyncio import run

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')


async def test():
    import ccxt.async_support as ccxt

    print('CCXT Version', ccxt.__version__)

    # local sandbox keys
    exchange = ccxt.hollaex({
        'apiKey': "YOUR_SANDBOX_API_KEY",
        'secret': "YOUR_SANDBOX_SECRET",
    })

    exchange.set_sandbox_mode(True)

    markets = await exchange.load_markets()

    exchange.verbose = True

    balance = await exchange.fetch_balance()
    print(f"balance: {balance}")

    await exchange.close()


run(test())
```

## High-Level Overview

This is a Python file located at `examples/py/async-hollaex-sandbox.py`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 19
- Comment lines: 2
- Blank lines: 13

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
python examples/py/async-hollaex-sandbox.py
```

