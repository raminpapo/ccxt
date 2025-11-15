# Documentation: examples/py/binance-ema.py

## File Metadata

- **Path**: `examples/py/binance-ema.py`
- **Size**: 757 bytes
- **Lines**: 31
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import pandas_ta as ta
import pandas as pd

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)


def main():
    exchange = ccxt.binance()
    markets = exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes
    ohlcv = exchange.fetch_ohlcv('BTC/USDT', '1m')
    if len(ohlcv):
        df = pd.DataFrame(ohlcv, columns=['timestamp', 'open', 'high', 'low', 'close', 'volume'])
        df['datetime'] = pd.to_datetime(df['timestamp'], unit='ms')
        ema = df.ta.ema()
        df = pd.concat([df, ema], axis=1)
        print(df)


main()

```

## High-Level Overview

This is a Python file located at `examples/py/binance-ema.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 19
- Comment lines: 2
- Blank lines: 10

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/binance-ema.py
```

