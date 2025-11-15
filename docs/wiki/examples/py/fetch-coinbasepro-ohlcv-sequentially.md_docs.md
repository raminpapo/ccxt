# Documentation: wiki/examples/py/fetch-coinbasepro-ohlcv-sequentially.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-coinbasepro-ohlcv-sequentially.md`
- **Size**: 980 bytes
- **Lines**: 39
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Coinbasepro Ohlcv Sequentially](./examples/py/)


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
exchange = ccxt.coinbasepro()
from_datetime = '2017-09-01 00:00:00'
from_timestamp = exchange.parse8601(from_datetime)
now = exchange.milliseconds()
data = []

while from_timestamp < now:

    try:

        print(exchange.milliseconds(), 'Fetching candles starting from', exchange.iso8601(from_timestamp))
        ohlcvs = exchange.fetch_ohlcv('BTC/USD', '1m', from_timestamp)
        print(exchange.milliseconds(), 'Fetched', len(ohlcvs), 'candles')
        from_timestamp = ohlcvs[-1][0]
        data += ohlcvs

    except (ccxt.ExchangeError, ccxt.AuthenticationError, ccxt.ExchangeNotAvailable, ccxt.RequestTimeout) as error:

        print('Got an error', type(error).__name__, error.args, ', retrying in', hold, 'seconds...')
        time.sleep(hold)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-coinbasepro-ohlcv-sequentially.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 25
- Comment lines: 2
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

