# Documentation: wiki/examples/py/async-okx-create-margin-order.md

## File Metadata

- **Path**: `wiki/examples/py/async-okx-create-margin-order.md`
- **Size**: 1,101 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Okx Create Margin Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.okx({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # okx requires this: https://github.com/ccxt/ccxt/wiki/Manual#authentication
        'password': 'YOUR_API_PASSWORD',
        # 'verbose': True,  # for debug output
    })
    try:
        # change the values here
        symbol = 'BTC/USDT'
        price = 123.45
        amount = 54.321
        type = 'limit'  # or market
        side = 'sell'
        order = await exchange.create_order(symbol, type, side, amount, price, {
            'margin': True,
            'marginMode': 'cross',
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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-okx-create-margin-order.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 33
- Comment lines: 4
- Blank lines: 10

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

**To execute this Markdown file:**

