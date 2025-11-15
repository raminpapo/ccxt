# Documentation: wiki/examples/py/async-fetch-ohlcv-multiple-symbols-continuously.md

## File Metadata

- **Path**: `wiki/examples/py/async-fetch-ohlcv-multiple-symbols-continuously.md`
- **Size**: 993 bytes
- **Lines**: 41
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Fetch Ohlcv Multiple Symbols Continuously](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from asyncio import run, gather

import ccxt.async_support as ccxt  # noqa: E402

print('CCXT Version:', ccxt.__version__)


async def fetch_ohlcv(exchange, symbol, timeframe, limit):
    since = None
    while True:
        try:
            ohlcv = await exchange.fetch_ohlcv(symbol, timeframe, since, limit)
            if len(ohlcv):
                first_candle = ohlcv[0]
                datetime = exchange.iso8601(first_candle[0])
                print(datetime, exchange.id, symbol, first_candle[1:])
        except Exception as e:
            print(type(e).__name__, str(e))


async def main():
    exchange = ccxt.binance()
    timeframe = '1m'
    limit = 1
    symbols = [ 'BTC/USDT', 'ETH/USDT' ]
    loops = [fetch_ohlcv(exchange, symbol, timeframe, limit) for symbol in symbols]
    await gather(*loops)
    await exchange.close()


run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-fetch-ohlcv-multiple-symbols-continuously.md`.

**Functions defined**: main, fetch_ohlcv

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 28
- Comment lines: 1
- Blank lines: 12

### Main Components

**Functions** (2):
- `fetch_ohlcv()`
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

