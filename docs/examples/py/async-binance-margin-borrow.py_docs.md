# Documentation: examples/py/async-binance-margin-borrow.py

## File Metadata

- **Path**: `examples/py/async-binance-margin-borrow.py`
- **Size**: 1,006 bytes
- **Lines**: 40
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
        # 'verbose': True,  # for debug output
    })
    await exchange.load_markets()
    code = 'BTC'
    amount = 1
    currency = exchange.currency(code)
    try:
        response = await exchange.sapi_post_margin_loan({
            'asset': currency['id'],
            'amount': exchange.currency_to_precision(code, amount)
        })
        pprint(response)
    except ccxt.InsufficientFunds as e:
        print('sapi_post_margin_loan() failed – not enough funds')
        print(e)
    except Exception as e:
        print('sapi_post_margin_loan() failed')
        print(e)
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-binance-margin-borrow.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 30
- Comment lines: 2
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
python examples/py/async-binance-margin-borrow.py
```

