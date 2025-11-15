# Documentation: wiki/examples/py/async-binance-create-trailing-percent-order.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-create-trailing-percent-order.md`
- **Size**: 1,386 bytes
- **Lines**: 53
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Create Trailing Percent Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.binanceusdm({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # 'verbose': True,  # for debug output
    })
    try:
        # change the values here
        symbol = 'BTC/USDT:USDT'
        type = 'market'
        side = 'sell'
        amount = 0.1
        price = None
        order = await exchange.create_order(symbol, type, side, amount, price, {
            'trailingPercent': 5,
            'reduceOnly': True,
            # 'trailingTriggerPrice': 45000,
        })
        # Or you can call the create_trailing_percent_order method:
        # trailing_percent = 5
        # trailing_trigger_price = 45000
        # params = {
        #     'reduceOnly': True,
        # }
        # order = await exchange.create_trailing_percent_order (symbol, type, side, amount, price, trailing_percent, trailing_trigger_price, params)
        pprint(order)
    except ccxt.InsufficientFunds as e:
        print('create_order() failed - not enough funds')
        print(e)
    except Exception as e:
        print('create_order() failed')
        print(e)
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-binance-create-trailing-percent-order.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 32
- Comment lines: 11
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

