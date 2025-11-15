# Documentation: wiki/examples/py/async-kucoin-rate-limit.md

## File Metadata

- **Path**: `wiki/examples/py/async-kucoin-rate-limit.md`
- **Size**: 1,197 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Kucoin Rate Limit](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from asyncio import run


import ccxt.async_support as ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)


async def main():
    exchange = ccxt.kucoin()
    markets = await exchange.load_markets()
    i = 0
    while True:
        try:
            symbol = 'BTC/USDT'
            timeframe = '5m'
            since = None
            limit = 1000
            ohlcvs = await exchange.fetch_ohlcv(symbol, timeframe, since, limit)
            now = exchange.milliseconds()
            datetime = exchange.iso8601(now)
            print(datetime, i, 'fetched', len(ohlcvs), symbol, timeframe, 'candles',
                'from', exchange.iso8601(ohlcvs[0][0]),
                'to', exchange.iso8601(ohlcvs[len(ohlcvs)-1][0]))
        except ccxt.RateLimitExceeded as e:
            now = exchange.milliseconds()
            datetime = exchange.iso8601(now)
            print(datetime, i, type(e).__name__, str(e))
            await exchange.sleep(10000)
        except Exception as e:
            print(type(e).__name__, str(e))
            raise e
        i += 1


run (main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-kucoin-rate-limit.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 34
- Comment lines: 1
- Blank lines: 12

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

