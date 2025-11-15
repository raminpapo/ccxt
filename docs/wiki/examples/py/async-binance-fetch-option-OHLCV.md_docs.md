# Documentation: wiki/examples/py/async-binance-fetch-option-OHLCV.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-fetch-option-OHLCV.md`
- **Size**: 1,307 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Fetch Option Ohlcv](./examples/py/)


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
    market_id = 'ETH-221028-1700-C'
    symbol = 'ETH/USDT:USDT-221028-1700-C'
    timeframe = '1m'
    since = 1592317127349
    limit = 10
    try:
        response = await exchange.fetch_OHLCV(symbol, timeframe, since, limit)
        # Implicit API:
        # response = await exchange.eapiPublicGetKlines({
        #     'symbol': market_id,
        #     'interval': timeframe,
        #     # 'startTime': since,  # optional
        #     # 'limit': limit,  # optional
        # })
        pprint(response)
    except Exception as e:
        print('fetch_OHLCV() failed')
        print(e)
    await exchange.close()


asyncio.run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-binance-fetch-option-OHLCV.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 27
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

