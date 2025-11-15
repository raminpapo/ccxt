# Documentation: examples/py/fetch_longer_ohlcv_through_multiple_calls_and_save_to_csv.py

## File Metadata

- **Path**: `examples/py/fetch_longer_ohlcv_through_multiple_calls_and_save_to_csv.py`
- **Size**: 1,124 bytes
- **Lines**: 54
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import ccxt  # noqa: E402
import numpy as np
from datetime import datetime

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

print('CCXT Version:', ccxt.__version__)

# data
exchange_name = 'ftx'
symbol = "BTC/USD"
max_candles = 5000
timeframe = '1h'
start = 1609459200000  # Jan 1, 2021
ms_per_candle = {
    '1m': 60000,
    '5m': 300000,
    '15m': 900000,
    '30m': 1800000,
    '1h': 3600000,
    '2h': 7200000,
    '4h': 14400000,
    '8h': 28800000,
    '12h': 57600000,
    '1d': 86400000,
}

now = int(datetime.now().timestamp() * 1000)
outfile = f"{symbol.replace('/', '-')}_{timeframe}_{exchange_name}_{start}-{now}.csv"

# setup
exchange = ccxt.ftx()
exchange.load_markets()
ohlcv = []

# make requests for candle data
while start < now:
    candles = exchange.fetch_ohlcv(symbol, timeframe, start, max_candles)
    ohlcv += candles
    start = start + (ms_per_candle[timeframe] * max_candles)

# write to csv
np.savetxt(
    outfile,
    ohlcv,
    delimiter=",",
    fmt='%d,%s,%s,%s,%s,%s'
)

```

## High-Level Overview

This is a Python file located at `examples/py/fetch_longer_ohlcv_through_multiple_calls_and_save_to_csv.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 40
- Comment lines: 5
- Blank lines: 9

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
python examples/py/fetch_longer_ohlcv_through_multiple_calls_and_save_to_csv.py
```

