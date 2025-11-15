# Documentation: examples/py/bitmex-fetch-ohlcv-with-extra-params.py

## File Metadata

- **Path**: `examples/py/bitmex-fetch-ohlcv-with-extra-params.py`
- **Size**: 1,008 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import time

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402

bitmex = ccxt.bitmex()

# params:
symbol = 'BTC/USD'
timeframe = '1m'
limit = 100
params = {'partial': False}  # ←--------  no reversal

while True:

    # pay attention to since with respect to limit if you're doing it in a loop
    since = bitmex.milliseconds() - limit * 60 * 1000

    candles = bitmex.fetch_ohlcv(symbol, timeframe, since, limit, params)
    num_candles = len(candles)
    print('{}: O: {} H: {} L:{} C:{}'.format(
        bitmex.iso8601(candles[num_candles - 1][0]),
        candles[num_candles - 1][1],
        candles[num_candles - 1][2],
        candles[num_candles - 1][3],
        candles[num_candles - 1][4]))
    # * 5 to make distinct delay and to avoid too much load
    # / 1000 to convert milliseconds to fractional seconds
    time.sleep(bitmex.rateLimit * 5 / 1000)

```

## High-Level Overview

This is a Python file located at `examples/py/bitmex-fetch-ohlcv-with-extra-params.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 22
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
python examples/py/bitmex-fetch-ohlcv-with-extra-params.py
```

