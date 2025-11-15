# Documentation: wiki/examples/py/poloniex-fetch-ohlcv-with-pagination.md

## File Metadata

- **Path**: `wiki/examples/py/poloniex-fetch-ohlcv-with-pagination.md`
- **Size**: 1,354 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Poloniex Fetch Ohlcv With Pagination](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402

exchange = ccxt.poloniex()
exchange.load_markets()

symbol = 'BTC/USDT'
timeframe = '5m'
since = exchange.parse8601('2024-01-01T00:00:00Z')
previous_length = 0
all_candles = []
limit = 500
duration = exchange.parse_timeframe(timeframe) * 1000
now = exchange.milliseconds()

while since < now:
    try:
        print('---------------------------------------------------------------')
        print('Fetching ohlcvs since', exchange.iso8601(since))
        endTime = since + duration * limit
        candles = exchange.fetch_ohlcv(symbol, timeframe, since, limit, {
            'until': endTime
        })
        print('Fetched', len(candles), 'candles')
        print('From', exchange.iso8601(candles[0][0]), 'to', exchange.iso8601(candles[-1][0]))
        since = candles[-1][0] + duration
        all_candles += candles
        total_length = len(all_candles)
        print('Fetched', total_length, 'candles in total')
    except ccxt.NetworkError as e:
        print(e)  # retry on next iteration
    except ccxt.ExchangeError as e:
        print(e)
        break

print('Fetched', len(all_candles), 'candles since', exchange.iso8601(all_candles[0][0]), 'till', exchange.iso8601(all_candles[-1][0]))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/poloniex-fetch-ohlcv-with-pagination.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 36
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

