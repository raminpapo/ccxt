# Documentation: examples/py/poloniex-fetch-ohlcv-with-pagination.py

## File Metadata

- **Path**: `examples/py/poloniex-fetch-ohlcv-with-pagination.py`
- **Size**: 1,396 bytes
- **Lines**: 44
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

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

## High-Level Overview

This is a Python file located at `examples/py/poloniex-fetch-ohlcv-with-pagination.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 35
- Comment lines: 1
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/poloniex-fetch-ohlcv-with-pagination.py
```

