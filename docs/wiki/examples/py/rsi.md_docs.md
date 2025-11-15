# Documentation: wiki/examples/py/rsi.md

## File Metadata

- **Path**: `wiki/examples/py/rsi.md`
- **Size**: 850 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Rsi](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import pandas_ta as ta
import pandas as pd
import ccxt
print('CCXT Version:', ccxt.__version__)

exchange = ccxt.binance()
symbol = 'BTC/USDT'
timeframe = '1m'
limit = 500
rsi_length = 100
while True:
    try:
        ohlcv = exchange.fetch_ohlcv(symbol, timeframe)
        print('--------------------------------------------------------------')
        if len(ohlcv):
            df = pd.DataFrame(ohlcv, columns=['time', 'open', 'high', 'low', 'close', 'volume'])
            df['time'] = pd.to_datetime(df['time'], unit='ms')
            df = pd.concat([df, df.ta.rsi(length=rsi_length)], axis=1)
            print(df[-20:])
            print(exchange.iso8601 (exchange.milliseconds()))
    except Exception as e:
        print(type(e).__name__, str(e))


 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/rsi.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 26
- Comment lines: 1
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

