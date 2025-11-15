# Documentation: examples/py/async-kucoin-rate-limit.py

## File Metadata

- **Path**: `examples/py/async-kucoin-rate-limit.py`
- **Size**: 1,252 bytes
- **Lines**: 44
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from asyncio import run

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

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

## High-Level Overview

This is a Python file located at `examples/py/async-kucoin-rate-limit.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 33
- Comment lines: 1
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

**To execute this Python file:**

```bash
python examples/py/async-kucoin-rate-limit.py
```

