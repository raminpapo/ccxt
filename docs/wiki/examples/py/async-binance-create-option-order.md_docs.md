# Documentation: wiki/examples/py/async-binance-create-option-order.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-create-option-order.md`
- **Size**: 1,482 bytes
- **Lines**: 53
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Create Option Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-
# This example uses the implicit API, in the future we will have options unified which will make things easier.
# You can check if the unified methods are ready-to-use (createOrder, fetchOrder etc) by checking: `is_unified = exchange.has['option']`

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


async def main():
    exchange = ccxt.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # 'verbose': True,  # for debug output
    })
    await exchange.load_markets()
    symbol = 'ETH/USDT:USDT-221028-1700-C'
    order_type = 'limit'
    side = 'buy'
    amount = 1
    price = 2.1
    try:
        response = await exchange.create_order(symbol, order_type, side, amount, price)
        # Implicit API:
        # response = await exchange.eapiPrivatePostOrder({
        #     # ETH/USDT call option strike 1700 USDT expiry on 2022-10-28
        #     'symbol': 'ETH-221028-1700-C',
        #     'side': 'BUY',
        #     'type': 'LIMIT',
        #     'quantity': 1,
        #     'price': 2.1,
        # })
        pprint(response)
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

This is a Markdown file located at `wiki/examples/py/async-binance-create-option-order.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 30
- Comment lines: 13
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

