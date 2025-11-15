# Documentation: wiki/examples/py/fetch-bitfinex-ohlcv-history.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-bitfinex-ohlcv-history.md`
- **Size**: 1,300 bytes
- **Lines**: 43
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Bitfinex Ohlcv History](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import time
import ccxt  # noqa: E402
# common constants

msec = 1000
minute = 60 * msec
hold = 30
exchange = ccxt.bitfinex()
from_datetime = '2017-01-01 00:00:00'
from_timestamp = exchange.parse8601(from_datetime)
now = exchange.milliseconds()
data = []

while from_timestamp < now:

    try:

        print(exchange.milliseconds(), 'Fetching candles starting from', exchange.iso8601(from_timestamp))
        ohlcvs = exchange.fetch_ohlcv('BTC/USD', '5m', from_timestamp)
        print(exchange.milliseconds(), 'Fetched', len(ohlcvs), 'candles')
        if len(ohlcvs) > 0:
            first = ohlcvs[0][0]
            last = ohlcvs[-1][0]
            print('First candle epoch', first, exchange.iso8601(first))
            print('Last candle epoch', last, exchange.iso8601(last))
            # from_timestamp += len(ohlcvs) * minute * 5  # very bad
            from_timestamp = ohlcvs[-1][0] + minute * 5  # good
            data += ohlcvs

    except (ccxt.ExchangeError, ccxt.AuthenticationError, ccxt.ExchangeNotAvailable, ccxt.RequestTimeout) as error:

        print('Got an error', type(error).__name__, error.args, ', retrying in', hold, 'seconds...')
        time.sleep(hold)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-bitfinex-ohlcv-history.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 30
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

