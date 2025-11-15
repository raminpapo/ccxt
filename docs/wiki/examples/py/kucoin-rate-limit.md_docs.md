# Documentation: wiki/examples/py/kucoin-rate-limit.md

## File Metadata

- **Path**: `wiki/examples/py/kucoin-rate-limit.md`
- **Size**: 998 bytes
- **Lines**: 42
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Kucoin Rate Limit](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)


exchange = ccxt.kucoin()
markets = exchange.load_markets()
i = 0
while True:
    try:
        symbol = 'BTC/USDT'
        timeframe = '5m'
        since = None
        limit = 1000
        ohlcvs = exchange.fetch_ohlcv(symbol, timeframe, since, limit)
        now = exchange.milliseconds()
        datetime = exchange.iso8601(now)
        print(datetime, i, 'fetched', len(ohlcvs), symbol, timeframe, 'candles',
            'from', exchange.iso8601(ohlcvs[0][0]),
            'to', exchange.iso8601(ohlcvs[len(ohlcvs)-1][0]))
    except ccxt.RateLimitExceeded as e:
        now = exchange.milliseconds()
        datetime = exchange.iso8601(now)
        print(datetime, i, type(e).__name__, str(e))
        exchange.sleep(10000)
    except Exception as e:
        print(type(e).__name__, str(e))
        raise e
    i += 1
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/kucoin-rate-limit.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 31
- Comment lines: 1
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

