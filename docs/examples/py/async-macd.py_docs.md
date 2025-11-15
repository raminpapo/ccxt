# Documentation: examples/py/async-macd.py

## File Metadata

- **Path**: `examples/py/async-macd.py`
- **Size**: 1,557 bytes
- **Lines**: 55
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import gather, run
import pandas_ta as ta
import pandas as pd
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402

# -----------------------------------------------------------------------------

print('CCXT Version:', ccxt.__version__)

# -----------------------------------------------------------------------------


async def run_ohlcv_loop(exchange, symbol, timeframe, limit):
    since = None
    fast = 12
    slow = 26
    signal = 9
    while True:
        try:
            ohlcv = await exchange.fetch_ohlcv(symbol, timeframe, since, limit)
            if len(ohlcv):
                df = pd.DataFrame(ohlcv, columns=['time', 'open', 'high', 'low', 'close', 'volume'])

                macd = df.ta.macd(fast=fast, slow=slow, signal=signal)
                df = pd.concat([df, macd], axis=1)
                print('----------------------------------------------------------')
                print(exchange.iso8601(exchange.milliseconds()), symbol, timeframe)
                print(df[-signal:])
        except Exception as e:
            print(type(e).__name__, str(e))


async def main():
    exchange = ccxt.binance()
    timeframe = '1m'
    limit = 50
    symbols = [
        'BTC/USDT',
        'ETH/USDT',
    ]
    loops = [run_ohlcv_loop(exchange, symbol, timeframe, limit) for symbol in symbols]
    await gather(*loops)
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/async-macd.py`.

**Functions defined**: main, run_ohlcv_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 38
- Comment lines: 3
- Blank lines: 14

### Main Components

**Functions** (2):
- `main()`
- `run_ohlcv_loop()`



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
python examples/py/async-macd.py
```

