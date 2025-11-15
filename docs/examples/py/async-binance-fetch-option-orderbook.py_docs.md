# Documentation: examples/py/async-binance-fetch-option-orderbook.py

## File Metadata

- **Path**: `examples/py/async-binance-fetch-option-orderbook.py`
- **Size**: 1,212 bytes
- **Lines**: 41
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-
# This example uses the implicit API, in the future we will have options unified which will make things easier.
# You can check if the unified methods are ready-to-use (createOrder, fetchOrder etc) by checking: `is_unified = exchange.has['option']`

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
    market_id = 'ETH-221028-1500-C'
    symbol = 'ETH/USDT:USDT-221028-1500-C'
    limit = 10
    try:
        response = await exchange.fetch_order_book(symbol, limit)
        # Implicit API:
        # response = await exchange.eapiPublicGetDepth({
        #     'symbol': market_id,
        #     # 'limit': limit,  # optional
        # })
        pprint(response)
    except Exception as e:
        print('fetch_order_book() failed')
        print(e)
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-binance-fetch-option-orderbook.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 24
- Comment lines: 9
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
python examples/py/async-binance-fetch-option-orderbook.py
```

