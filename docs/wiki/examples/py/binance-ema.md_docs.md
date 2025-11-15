# Documentation: wiki/examples/py/binance-ema.md

## File Metadata

- **Path**: `wiki/examples/py/binance-ema.md`
- **Size**: 690 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Ema](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import pandas_ta as ta
import pandas as pd


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-ema.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 20
- Comment lines: 2
- Blank lines: 12

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

**To execute this Markdown file:**

