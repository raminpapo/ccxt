# Documentation: wiki/examples/py/async-binance-cancel-option-order.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-cancel-option-order.md`
- **Size**: 1,177 bytes
- **Lines**: 44
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Cancel Option Order](./examples/py/)


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
    market_id = 'ETH-230214-1525-C'
    symbol = 'ETH/USDT:USDT-230214-1525-C'
    order_id = 4612100534317768959
    try:
        response = await exchange.cancel_order(order_id, symbol)
        # Implicit API:
        # response = await exchange.eapiPrivateDeleteOrder({
        #     'symbol': market_id,
        #     'orderId': order_id,
        # })
        pprint(response)
    except Exception as e:
        print('cancel_order() failed')
        print(e)
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-binance-cancel-option-order.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 25
- Comment lines: 9
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

