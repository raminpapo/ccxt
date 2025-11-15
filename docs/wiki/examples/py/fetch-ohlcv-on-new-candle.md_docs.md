# Documentation: wiki/examples/py/fetch-ohlcv-on-new-candle.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-ohlcv-on-new-candle.md`
- **Size**: 1,448 bytes
- **Lines**: 44
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Ohlcv On New Candle](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import time
import ccxt  # noqa: E402
from ccxt.base.decimal_to_precision import ROUND_UP  # noqa: E402
# common constants

msec = 1000
minute = 60 * msec
hold = 30
exchange = ccxt.binance()

limit = 500
timeframe = "5m"
interval = exchange.parse_timeframe(timeframe) * 1000

while True:

    try:

        print(exchange.milliseconds(), 'Fetching candles')
        since = exchange.round_timeframe(timeframe, exchange.milliseconds(), ROUND_UP) - (limit * interval)
        ohlcv = exchange.fetch_ohlcv('ETH/BTC', timeframe, since=since, limit=limit)
        print(exchange.milliseconds(), 'Fetched', len(ohlcv), 'candles')
        first = ohlcv[0][0]
        last = ohlcv[-1][0]
        print('First candle epoch', first, exchange.iso8601(first))
        print('Last candle epoch', last, exchange.iso8601(last))
        # Calculate time to next candle and sleep for that many seconds
        sleeptime = (exchange.round_timeframe(timeframe, last, ROUND_UP) - exchange.milliseconds()) / 1000
        print('sleeping for: ', sleeptime, 's', sleeptime // 60, 'min')
        time.sleep(sleeptime)
    except (ccxt.ExchangeError, ccxt.AuthenticationError, ccxt.ExchangeNotAvailable, ccxt.RequestTimeout) as error:

        print('Got an error', type(error).__name__, error.args, ', retrying in', hold, 'seconds...')
        time.sleep(hold)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-ohlcv-on-new-candle.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 31
- Comment lines: 3
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

