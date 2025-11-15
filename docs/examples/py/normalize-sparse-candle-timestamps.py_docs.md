# Documentation: examples/py/normalize-sparse-candle-timestamps.py

## File Metadata

- **Path**: `examples/py/normalize-sparse-candle-timestamps.py`
- **Size**: 672 bytes
- **Lines**: 33
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402

exchange = ccxt.binance()

symbol = 'ETH/BTC'
timeframe = '1h'

candles = exchange.fetch_ohlcv(symbol, timeframe)

# timeframe duration in seconds
duration = exchange.parse_timeframe(timeframe)

# timeframe duration in milliseconds
duration *= 1000

pprint([[
    exchange.iso8601(int(round(candle[0] / duration)) * duration),
    candle[1],  # o
    candle[2],  # h
    candle[3],  # l
    candle[4],  # c
    candle[5]   # v
] for candle in candles])

```

## High-Level Overview

This is a Python file located at `examples/py/normalize-sparse-candle-timestamps.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 20
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

**To execute this Python file:**

```bash
python examples/py/normalize-sparse-candle-timestamps.py
```

