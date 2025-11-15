# Documentation: examples/py/async-binance-create-margin-order.py

## File Metadata

- **Path**: `examples/py/async-binance-create-margin-order.py`
- **Size**: 987 bytes
- **Lines**: 41
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
    try:
        # change the values here
        symbol = 'BTC/USDT'
        price = 9000
        amount = 1
        type = 'limit'  # or market
        side = 'buy'
        order = await exchange.create_order(symbol, type, side, amount, price, {
            'type': 'margin',
        })
        pprint(order)
    except ccxt.InsufficientFunds as e:
        print('create_order() failed – not enough funds')
        print(e)
    except Exception as e:
        print('create_order() failed')
        print(e)
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-binance-create-margin-order.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 30
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
python examples/py/async-binance-create-margin-order.py
```

